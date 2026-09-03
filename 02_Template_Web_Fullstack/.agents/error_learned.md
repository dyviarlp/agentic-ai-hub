# Matriz Maestra de Aprendizaje de Errores (.agents/error_learned.md)

> **Gobernanza del Agente:** Sistema de Memoria Modular Particionada (RAG Jerárquico) para Web Fullstack & Cloud.  
> **Directriz de Consulta:** Antes de crear componentes, modificar estilos o alterar rutas de backend, consulta la regla preventiva y accede a la ficha temática en `.agents/memory/`.

---

## ⚡ Matriz de Consulta Rápida por Dominios

| ID | Dominio | Síntoma / Riesgo Clave | Regla Preventiva Inmutable | Ficha Detallada |
| :--- | :--- | :--- | :--- | :---: |
| **MEM-01** | Anti-Overfetching | Barrido masivo de componentes `.tsx` ante preguntas sobre textos, servicios o valor | Enrutar directamente a `web_services_catalog` (`06_web_services_catalog.md`). Cero inspección de código UI para contenido. | [06_web_services_catalog.md](memory/06_web_services_catalog.md) |
| **MEM-02** | Core Web Vitals | Degradación de LCP (>2s) por imágenes pesadas o scripts de terceros bloqueantes | Atributo `priority` en hero image, `next/image` con tamaños declarados y scripts diferidos con `strategy="lazyOnload"`. | [01_core_web_vitals_perf.md](memory/01_core_web_vitals_perf.md) |
| **MEM-03** | UI/UX Pro Max | Interfaces genéricas, esquemas de color planos o tipografía básica del navegador | Paletas HSL oscuras curadas, tipografía moderna de Google Fonts, glassmorphism y micro-interacciones fluidas. | [02_ui_ux_design_system.md](memory/02_ui_ux_design_system.md) |
| **MEM-04** | Strict TypeScript | Uso de `any`, aserciones `as unknown` o contratos de API no validados en runtime | Tipado estricto sin excepciones; validación obligatoria con esquemas Zod en todas las fronteras de entrada/salida. | [03_typescript_api_contracts.md](memory/03_typescript_api_contracts.md) |
| **MEM-05** | Accessibility (a11y) | Errores de contraste de color o navegación por teclado rota en modales y menús | Cumplimiento estricto WCAG AA, atributos ARIA requeridos y foco accesible gestionado. | [04_seo_meta_a11y.md](memory/04_seo_meta_a11y.md) |
