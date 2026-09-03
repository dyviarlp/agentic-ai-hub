# Matriz Maestra de Aprendizaje de Errores (.agents/error_learned.md)

> **Gobernanza del Agente:** Sistema de Memoria Modular Particionada (RAG Jerárquico) para Flutter Mobile.  
> **Directriz de Consulta:** Antes de modificar modelos, screens o providers de Riverpod, consulta la regla preventiva y accede a la ficha temática en `.agents/memory/`.

---

## ⚡ Matriz de Consulta Rápida por Dominios

| ID | Dominio | Síntoma / Riesgo Clave | Regla Preventiva Inmutable | Ficha Detallada |
| :--- | :--- | :--- | :--- | :---: |
| **MEM-01** | Anti-Overfetching | Barrido indiscriminado de widgets Dart para buscar textos de la app o features | Enrutar directamente a `app_features_catalog` (`06_app_features_catalog.md`). Cero escaneo ciego de `lib/`. | [06_app_features_catalog.md](memory/06_app_features_catalog.md) |
| **MEM-02** | Core Logic | Desbordamiento de nulos en runtime o excepciones `NullPointerException` | Clases de dominio 100% inmutables (`@immutable`), constructores `const` y colecciones nulas mapeadas a `const []`. | [01_core_logic.md](memory/01_core_logic.md) |
| **MEM-03** | UI Resilience | Excepciones `RenderFlex overflowed by X pixels` en pantallas de pantalla pequeña | Uso de `LayoutBuilder`, `SingleChildScrollView` y tipografía adaptable con `MediaQuery`. | [02_ui_components.md](memory/02_ui_components.md) |
| **MEM-04** | State Leaks | Re-renderizados masivos de árbol de widgets o fugas de listeners en Riverpod | Suscripciones quirúrgicas mediante `ref.watch(provider.select(...))` y disposición limpia de controladores. | [03_state_providers.md](memory/03_state_providers.md) |
| **MEM-05** | Obfuscation | Compilación de release sin ofuscación de código expuesta a ingeniería inversa | Compilación obligatoria con `--obfuscate --split-debug-info` según OWASP MASVS v2.0. | [05_governance_evidence.md](memory/05_governance_evidence.md) |
