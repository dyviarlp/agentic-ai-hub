# Memoria de Dominio 06: Catálogo de Funcionalidades & Textos Legales (Blueprint)

> Última validación: 2026-09-03 | Estado: Plantilla Oficial Enterprise Hub  
> Single Source of Truth (SSOT) para funcionalidades de la app, textos legales obligatorios y tiers de monetización.  
> Desacoplado del árbol de widgets en Dart (`lib/`).

---

## 📋 Catálogo Estructurado de Funcionalidades Móviles

| Módulo / Capacidad | Descripción Técnica | Invariante de Seguridad / UX |
| :--- | :--- | :--- |
| **Autenticación & Sesión** | Firebase Auth con persistencia local segura | Token refresh automático, biometría opcional, zero session leaks. |
| **Caché & Modo Offline** | Almacenamiento local SQLite / Hive desacoplado | Sincronización asíncrona en segundo plano con compuerta de reintentos. |
| **Descargos Legales Obligatorios** | Avisos de privacidad y compliance regulatorio | Descargo visible previo a acciones críticas; aceptación registrada con timestamp. |
| **Monetización & Suscripciones** | In-App Purchases / RevenueCat / AdMob | Fallback graceful en modo offline; restauración determinista de compras. |

---

## ⚡ Directrices Anti-Overfetching para el Agente Móvil

1. **Consulta de Textos y Features:** Ante preguntas sobre qué hace la app, textos de advertencia o estructura de planes, el agente debe consultar este catálogo (`06_app_features_catalog.md`) en lugar de escanear widgets Dart en `lib/`.
2. **Prohibición de Barrido en Código:** Prohibido ejecutar `view_file` sobre toda la carpeta de screens o providers solo para extraer strings de la interfaz.
