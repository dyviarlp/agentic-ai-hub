# Matriz Maestra de Aprendizaje de Errores (.agents/error_learned.md)

> **Gobernanza del Agente:** Sistema de Memoria Modular Particionada (RAG JerÃ¡rquico).  
> **Directriz de Consulta:** Antes de refactorizar un mÃ³dulo, consulta la regla preventiva en la matriz y accede a la ficha temÃ¡tica correspondiente en `.agents/memory/`.

---

## âš¡ Matriz de Consulta RÃ¡pida por Dominios

| ID | Dominio | SÃ­ntoma / Riesgo Clave | Regla Preventiva Inmutable | Ficha Detallada |
| :--- | :--- | :--- | :--- | :---: |
| **MEM-01** | Core & State | Fuga de memoria en streams de Notifiers | Registrar formalmente `ref.onDispose(() => sub.cancel())`. | [03_state_providers.md](memory/03_state_providers.md) |
| **MEM-02** | Storage | Fuga de memoria o crash por archivos temporales grandes | Usar siempre `putData(bytes)` en flujos de memoria en lugar de rutas fÃ­sicas. | [04_data_storage.md](memory/04_data_storage.md) |
| **MEM-03** | UI & Layout | RenderFlex overflow en teclados o fuentes grandes | Layouts scrollables seguros con `SingleChildScrollView` y envolver en `SafeArea`. | [02_ui_components.md](memory/02_ui_components.md) |
