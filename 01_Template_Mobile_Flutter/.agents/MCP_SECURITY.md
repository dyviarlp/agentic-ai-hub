# Protocolo de Seguridad y Revocación de Servidores MCP

Documento de referencia para la gestión segura de credenciales asociadas a los Servidores MCP configurados en el entorno de MascotIA. Este documento debe revisarse trimestralmente y actualizarse ante cualquier cambio de personal o incidente de seguridad.

---

## Principio de Mínimo Privilegio

> [!CAUTION]
> Ningún token o credencial de MCP debe tener permisos de escritura o borrado en producción sin confirmación explícita del usuario. En caso de duda, revocar y regenerar el token.

---

## Registro de MCPs y Credenciales

### GitHub MCP (Fase 2)

| Campo | Valor |
| :--- | :--- |
| **Permisos autorizados** | Lectura de repositorio, creación de PRs e issues. Sin acceso a Settings, Webhooks ni Collaborators. |
| **Tipo de credencial** | Personal Access Token (PAT) con scope `repo:read`, `pull_requests:write`, `issues:write` |
| **Dónde revocar** | [GitHub Settings → Developer Settings → Personal Access Tokens](https://github.com/settings/tokens) |
| **Dónde almacenar** | Variable de entorno local del sistema (`$env:GITHUB_PERSONAL_ACCESS_TOKEN`). Nunca en `.env` ni commiteado. |
| **Política de rotación** | Cada 90 días o inmediatamente si se detecta uso no autorizado. |

### Firebase / GCP MCP (Fase 2)

| Campo | Valor |
| :--- | :--- |
| **Permisos autorizados** | Lectura de Firestore, Storage (listado). Cero escritura/borrado en producción sin confirmación explícita. |
| **Tipo de credencial** | Service Account Key con rol `roles/datastore.viewer` + `roles/storage.objectViewer` |
| **Dónde revocar** | [Firebase Console → Project Settings → Service Accounts](https://console.firebase.google.com) → Desactivar clave |
| **Dónde almacenar** | Variable de entorno local (`$env:FIREBASE_MCP_CREDENTIALS`). Nunca en el repositorio. |
| **Política de rotación** | Cada 90 días o inmediatamente si el fichero de clave queda expuesto. |

### Crashlytics / Telemetría MCP (Fase 3)

| Campo | Valor |
| :--- | :--- |
| **Permisos autorizados** | Solo lectura de informes de errores y sesiones de Crashlytics. |
| **Tipo de credencial** | API Key de Firebase con restricción de IP o dominio local. |
| **Dónde revocar** | [Google Cloud Console → APIs & Services → Credentials](https://console.cloud.google.com/apis/credentials) |
| **Política de rotación** | Cada 90 días. |

---

## Protocolo de Respuesta ante Incidente de Credenciales

Si se sospecha que un token ha quedado expuesto (commit accidental, log visible, captura de pantalla):

1. **Revocar inmediatamente** el token desde el panel correspondiente (enlaces arriba).
2. Ejecutar `git log --all --full-history --grep="token\|key\|secret"` para verificar que no quedó commiteado.
3. Si el token aparece en el historial de Git, usar `git filter-repo` para eliminarlo del historial completo.
4. Regenerar el token con los mismos permisos mínimos.
5. Actualizar la variable de entorno local y verificar que el nuevo MCP conecta correctamente.
6. Registrar el incidente en `.agents/error_learned.md` con ID `SEC-XXX`.
