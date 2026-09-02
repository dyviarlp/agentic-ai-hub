# Matriz Maestra de Aprendizaje de Errores (.agents/error_learned.md)

> **Gobernanza del Agente:** Sistema de Memoria Modular Particionada (RAG Jerárquico) para Career & HR Strategy.  
> **Directriz de Consulta:** Antes de modificar maquetaciones, plantillas HTML/CSS o redacción de perfiles, consulta la regla preventiva y accede a la ficha temática en `.agents/memory/`.

---

## ⚡ Matriz de Consulta Rápida por Dominios

| ID | Dominio | Síntoma / Riesgo Clave | Regla Preventiva Inmutable | Ficha Detallada |
| :--- | :--- | :--- | :--- | :---: |
| **MEM-01** | Playwright Engine | Desbordamiento silencioso a página 3 o texto oculto por `overflow: hidden` | Paginación determinista en 2 páginas A4 exactas (210x297mm) y auditoría con `fitz` del último bloque de texto. | [02_playwright_engine.md](memory/02_playwright_engine.md) |
| **MEM-02** | Confidentiality | Fuga de datos confidenciales o nombres de clientes protegidos por NDA | Abstracción absoluta: utilizar roles profesionales genéricos y proyectos independientes. Cero PII. | [03_confidentiality_governance.md](memory/03_confidentiality_governance.md) |
| **MEM-03** | ATS Optimization | Pérdida de indexación en parsers ATS por tablas complejas o keywords no normalizadas | Jerarquía semántica plana, tipografía estándar y keywords tecnológicas estandarizadas de la industria. | [01_ats_optimization.md](memory/01_ats_optimization.md) |
| **MEM-04** | Cross-Project Audit | Intentar editar código de aplicaciones o proyectos externos desde el espacio de perfiles | Invariante Zero-Touch: Solo herramientas de inspección pasiva (`view_file`, `grep_search`). Cero escritura externa. | [04_cross_project_audit.md](memory/04_cross_project_audit.md) |
| **MEM-05** | Personal Branding | Uso de clichés de IA ("delve", "testament") o afirmaciones sin métricas | Activación obligatoria de `humanizer` y justificación cuantitativa de cada logro técnico. | [01_ats_optimization.md](memory/01_ats_optimization.md) |
