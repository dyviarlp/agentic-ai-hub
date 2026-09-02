# Protocolo de Seguridad y Gobernanza de Servidores MCP (Career Engine & HR Strategy)

Documento normativo para la gestión segura de herramientas y credenciales asociadas a los Servidores MCP en proyectos de **Generación de Perfiles Profesionales y Estrategia de Carrera**. Revisión trimestral obligatoria.

---

## 1. Principio de Privacidad Absoluta y Protección de Datos (RGPD / PII)

> [!CAUTION]
> La información tratada en perfiles profesionales incluye datos personales, trayectorias laborales y métricas de desempeño confidenciales.
> Queda terminantemente prohibido exfiltrar información personal identificable (PII) o datos sensibles a servicios de terceros sin anonimización previa.

---

## 2. Registro de Servidores MCP y Credenciales

### Chrome DevTools / Playwright Headless MCP

| Parámetro | Definición Normativa |
| :--- | :--- |
| **Finalidad Operativa** | Renderizado headless y verificación visual estricta de documentos A4 (exactamente 2 páginas, cero desbordamiento visual). |
| **Permisos Autorizados** | Ejecución en entorno local cerrado de generación de PDF. Cero tráfico de red saliente hacia dominios externos durante el renderizado. |
| **Restricciones Críticas** | Prohibido transmitir contenido del DOM del currículum a servicios analíticos no autorizados. |
| **Política de Rotación** | Sesión efímera de navegador local. |

### GitHub MCP (Versionado de Releases Oficiales)

| Parámetro | Definición Normativa |
| :--- | :--- |
| **Finalidad Operativa** | Control de versiones, etiquetado semántico y releases de currículums en PDF aprobados por Juan Armando. |
| **Permisos Autorizados** | `repo:read`, `pull_requests:write`. Restringido al repositorio de perfiles profesionales. |
| **Tipo de Credencial** | GitHub Personal Access Token (PAT). |
| **Dónde Almacenar** | Variable de entorno local del sistema (`$env:GITHUB_PERSONAL_ACCESS_TOKEN`). |
| **Dónde Revocar** | [GitHub Settings → Developer Settings → Personal Access Tokens](https://github.com/settings/tokens) |
| **Política de Rotación** | Cada 90 días. |

---

## 3. Invariantes de Gobernanza

1. **Aislamiento de Proyectos:** Prohibido modificar o leer archivos fuera del árbol del proyecto (`zero_touch_external_projects`).
2. **Cero Leaks de PII:** Ningún dato de contacto privado ni información salarial debe enviarse a través de endpoints MCP públicos.
