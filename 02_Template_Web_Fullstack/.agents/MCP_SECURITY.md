# Protocolo de Seguridad y Gobernanza de Servidores MCP (Web Fullstack & Cloud)

Documento normativo para la gestión segura de herramientas y credenciales asociadas a los Servidores MCP (**Model Context Protocol**) en proyectos **Web Fullstack & Cloud**. Revisión trimestral obligatoria.

---

## 1. Principio de Mínimo Privilegio

> [!CAUTION]
> Todas las herramientas MCP operan con permisos acotados y control de acceso estricto. Queda prohibida la ejecución de scripts no auditados en entornos de producción o la exposición de credenciales en el cliente web.

---

## 2. Registro de Servidores MCP y Credenciales

### Chrome DevTools MCP (Browser Testing & CWV)

| Parámetro | Definición Normativa |
| :--- | :--- |
| **Finalidad Operativa** | Auditoría automatizada de accesibilidad (a11y), inspección del árbol DOM, captura de errores de consola y medición de Core Web Vitals (LCP, INP, CLS). |
| **Permisos Autorizados** | Navegación e inspección restringida a entornos locales (`http://localhost:*`, `http://127.0.0.1:*`) y URLs de staging autorizadas. |
| **Restricciones Críticas** | Prohibido interactuar con páginas bancarias, portales externos de autenticación o inyectar JavaScript en sitios ajenos. |
| **Política de Rotación** | No aplica token persistente; sesión efímera controlada por DevTools CDP. |

### GitHub MCP (Control de Versiones y Despliegues)

| Parámetro | Definición Normativa |
| :--- | :--- |
| **Finalidad Operativa** | Gestión de ramas, creación de Pull Requests para componentes frontend y seguimiento de issues. |
| **Permisos Autorizados** | Scopes mínimos: `repo:read`, `pull_requests:write`, `issues:write`. Sin acceso administrativo a Settings ni Webhooks. |
| **Tipo de Credencial** | GitHub Personal Access Token (PAT). |
| **Dónde Almacenar** | Variable de entorno local del sistema (`$env:GITHUB_PERSONAL_ACCESS_TOKEN`). Nunca en `.env` ni commiteado. |
| **Dónde Revocar** | [GitHub Settings → Developer Settings → Personal Access Tokens](https://github.com/settings/tokens) |
| **Política de Rotación** | Cada 90 días o ante cualquier sospecha de filtración. |

---

## 3. Protocolo de Respuesta ante Incidente de Credenciales

1. **Revocación Inmediata:** Anular el token comprometido en GitHub Developer Settings.
2. **Escaneo Git:** Ejecutar escaneo forense de secretos locales para confirmar que no se versionó.
3. **Regeneración de Credencial:** Emitir un nuevo token con alcances mínimos idénticos.
4. **Actualización Segura:** Actualizar `$env:GITHUB_PERSONAL_ACCESS_TOKEN` en la máquina local.
