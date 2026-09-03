# Matriz Maestra de Aprendizaje de Errores (.agents/error_learned.md)

> **Gobernanza del Agente:** Sistema de Memoria Modular Particionada (RAG Jerárquico) para AI Safety & Security Audits.  
> **Directriz de Consulta:** Antes de iniciar auditorías, red teaming o evaluaciones de modelos, consulta la regla preventiva y accede a la ficha temática en `.agents/memory/`.

---

## ⚡ Matriz de Consulta Rápida por Dominios

| ID | Dominio | Síntoma / Riesgo Clave | Regla Preventiva Inmutable | Ficha Detallada |
| :--- | :--- | :--- | :--- | :---: |
| **MEM-01** | Anti-Overfetching | Barrido indiscriminado de directorios mediante `view_file` o `grep_search` | Enrutar consultas exclusivamente a través de los dominios de `project_manifest.json`. Prohibido el escaneo ciego de archivos no indexados. | [AGENTS.md](AGENTS.md) |
| **MEM-02** | Anti-Stale Guard | Aplicación de contramedidas o remediaciones de seguridad desfasadas | Verificar encabezado `> Última validación: YYYY-MM-DD` antes de validar cualquier vector de ataque o regla cloud. | [02_mitigations_playbook.md](memory/02_mitigations_playbook.md) |
| **MEM-03** | Zero-Touch Policy | Intentar modificar código o archivos en repositorios externos | Inspección estrictamente pasiva (`read-only`). Cero escritura o modificación de código externo desde este workspace. | [01_vulnerabilities_registry.md](memory/01_vulnerabilities_registry.md) |
| **MEM-04** | Evidence Gate | Emitir veredictos de seguridad sin pruebas reproducibles o métricas cuantificables | Safety Score mínimo $\ge 95\%$, cero vulnerabilidades críticas sin mitigar y parches exactos documentados. | [03_llm_evals_benchmarks.md](memory/03_llm_evals_benchmarks.md) |
| **MEM-05** | Audit Reports SSOT | Explorar carpetas de reportes históricos a ciegas para contrastar resultados pasados | Consultar quirúrgicamente el índice maestro de informes de auditoría (`06_audit_reports_index.md`). | [06_audit_reports_index.md](memory/06_audit_reports_index.md) |
