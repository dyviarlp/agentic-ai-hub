# Protocolo de Seguridad y Gobernanza de Servidores MCP (AI Safety & Audit)

Documento normativo para la gestión segura de herramientas y credenciales asociadas a los Servidores MCP (**Model Context Protocol**) en proyectos de **Auditoría y AI Safety Evals**. Revisión trimestral obligatoria.

---

## 1. Principio de Mínimo Privilegio y Modo Solo-Lectura

> [!CAUTION]
> Todas las herramientas MCP utilizadas en procesos de auditoría y evaluación de seguridad operan bajo el principio de **Solo-Lectura (Read-Only)**.
> Queda terminantemente prohibido autorizar permisos de mutación, escritura o borrado en bases de datos Firestore, buckets de Storage o repositorios de producción sin validación humana explícita.

---

## 2. Registro de Servidores MCP y Matriz de Privilegios

### Hugging Face Hub MCP (Evals & Benchmarks)

| Parámetro | Definición Normativa |
| :--- | :--- |
| **Finalidad Operativa** | Descarga e inspección de datasets de red teaming, taxonomías de jailbreak, benchmarks de factualidad y pesos/modelos de referencia. |
| **Permisos Autorizados** | Solo lectura (`read`). Consulta de modelos, datasets, Spaces y papers técnicos. |
| **Tipo de Credencial** | Hugging Face Access Token con scope de lectura (`read`). |
| **Dónde Almacenar** | Variable de entorno local del sistema (`$env:HF_TOKEN`). Prohibido en `.env` o en disco. |
| **Dónde Revocar** | [Hugging Face Settings → Access Tokens](https://huggingface.co/settings/tokens) |
| **Política de Rotación** | Cada 90 días o tras sospecha de compromiso. |

### GitHub MCP (Auditoría Estática de Código)

| Parámetro | Definición Normativa |
| :--- | :--- |
| **Finalidad Operativa** | Inspección de repositorios, auditoría de commits, validación de diffs en Pull Requests y detección de secretos. |
| **Permisos Autorizados** | `repo:read`, `pull_requests:read`. Cero permisos sobre `settings`, `webhooks`, `admin` o borrado de ramas. |
| **Tipo de Credencial** | GitHub Personal Access Token (Fine-grained o Classic) restringido al rol de auditor. |
| **Dónde Almacenar** | Variable de entorno local del sistema (`$env:GITHUB_PERSONAL_ACCESS_TOKEN`). |
| **Dónde Revocar** | [GitHub Settings → Developer Settings → Personal Access Tokens](https://github.com/settings/tokens) |
| **Política de Rotación** | Cada 90 días. |

### Firebase & Cloud Security Auditor MCP

| Parámetro | Definición Normativa |
| :--- | :--- |
| **Finalidad Operativa** | Auditoría estática y dinámica de reglas de seguridad (`firestore.rules`, `storage.rules`) y esquemas de datos. |
| **Permisos Autorizados** | Roles estrictos de visor: `roles/datastore.viewer` y `roles/storage.objectViewer`. Cero acceso de edición. |
| **Tipo de Credencial** | Service Account Key de auditoría o Firebase CLI OAuth local (`firebase login`). |
| **Dónde Almacenar** | Variable de entorno local (`$env:FIREBASE_MCP_CREDENTIALS`) o almacén local cifrado del CLI. |
| **Dónde Revocar** | [Google Cloud Console → IAM & Admin → Service Accounts](https://console.cloud.google.com/iam-admin/serviceaccounts) |
| **Política de Rotación** | Cada 90 días. |

---

## 3. Protocolo de Respuesta ante Incidente de Credenciales (SEC-IRP)

1. **Revocación Inmediata:** Desactivar de forma instantánea el token desde la consola del proveedor (GitHub, Hugging Face, GCP).
2. **Escaneo Forense Local:** Ejecutar `python scripts/audit_zero_secrets.py` para verificar el alcance de la exposición.
3. **Saneamiento de Historial Git:** Si el token fue comprometido en Git, purgarlo usando `git filter-repo` o desindexar con `git rm --cached`.
4. **Regeneración de Credencial:** Emitir un nuevo token con permisos mínimos estrictos.
5. **Registro en Memoria:** Abrir ficha de incidente en `.agents/memory/01_vulnerabilities_registry.md`.
