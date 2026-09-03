# Memoria de Dominio 06: Índice Maestro de Informes de Auditoría (Blueprint)

> Última validación: 2026-09-03 | Estado: Plantilla Oficial Enterprise Hub  
> Catálogo canónico de informes técnicos de seguridad, evaluaciones de modelos LLM y certificaciones de ecosistema.

---

## 📋 Catálogo de Informes en `audit_reports/`

| Archivo de Informe | Fecha de Ejecución | Ámbito de Inspección | Score / Veredicto | Hallazgos Clave |
| :--- | :---: | :--- | :---: | :--- |
| `CROSS_PROJECT_ECOSYSTEM_AUDIT_2026.md` | 2026-09-02 | Ecosistema completo (Manifiestos, dominios RAG) | **100/100 (Enterprise Gold)** | Manifiestos RFC 8259 conformes, 0 skills fantasma, 0 secretos expuestos, tests alineados. |
| `MCP_ECOSYSTEM_AUDIT_2026.md` | 2026-09-02 | Gobernanza MCP, credenciales y privilegios | **100/100 (Aprobado)** | Aislamiento mínimo privilegio (Read-Only en Evals, Localhost en Web), rotación 90 días. |

---

## ⚡ Directrices de Consulta RAG (Anti-Overfetching)

1. **Consulta Histórica Quirúrgica:** Ante preguntas sobre puntuaciones pasadas o vulnerabilidades resueltas, el agente debe consultar este índice (`06_audit_reports_index.md`) antes de abrir informes completos.
2. **Prohibición de Barrido Ciego:** Prohibido listar o escanear archivos no indexados en `audit_reports/` mediante `view_file` o `grep_search` indiscriminados.
3. **Consistencia de Métricas:** Todo dato citado sobre versiones, pass rate o conformidades debe contrastarse con este registro consolidado.
