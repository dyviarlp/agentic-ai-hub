# Ficha Técnica: Protocolo de Lectura Inteligente Pasiva & Zero-Touch Policy

> Última validación: 2026-09-02  
> Dominio: Cross-Project Passive Observability & Zero-Touch Engineering Audit

---

## 1. El Principio de Lectura Inteligente (Smart Read-Only)

El agente de perfiles profesionales y estrategia de carrera actúa como un **auditor técnico pasivo**:
- **Misión:** Rastrear, extraer e interpretar evidencias reales de ingeniería y producción directamente desde los repositorios de proyectos adyacentes (`../MascotIA`, `../Agent Hub & Template Repository`, u otros proyectos futuros).
- **Invariante Absoluta (Zero-Touch):** **PROHIBIDO MODIFICAR O ESCRIBIR CÓDIGO EXTERNO.** Toda interacción con proyectos fuera de `PERFILES PROFESIONALES (CV)` se realiza con herramientas exclusivas de inspección (`view_file`, `grep_search`, `list_dir`). Jamás ejecutar comandos destructivos, linters de escritura o herramientas de edición sobre repositorios de desarrollo.

---

## 2. Puntos Clave de Inspección Cruzada (Inspection Vectors)

Para descubrir nuevos hitos sin intervención manual, el agente debe auditar los siguientes vectores:

| Vector de Inspección | Archivos Típicos | Señal Técnica a Extraer |
| :--- | :--- | :--- |
| **Notas de Versión y Despliegue** | `RELEASE_NOTES*.md`, `CHANGELOG.md` | Versión semántica (`v1.0.0+40`), pista de despliegue (Producción / Closed Beta), fechas de release, superación de requisitos de tiendas (14 días con 20 testers). |
| **Garantía de Calidad (QA)** | `test/`, reportes de cobertura, `lcov.info` | Cobertura de tests, volumen de pruebas aprobadas (`108/108 tests`), ausencia de warnings/errores en análisis estático. |
| **Arquitectura y Manifiestos** | `pubspec.yaml`, `package.json`, `AndroidManifest.xml` | Versiones de frameworks (Flutter 3.5+, Dart 3.5+, Android API 34–37), dependencias críticas (Firebase, Riverpod 3.x), permisos y directivas de seguridad (`tools:node="remove"`). |
| **Ingeniería Forense & Parches** | Comentarios en código nativo, logs, `build.gradle` | Crashes resueltos a bajo nivel, desensamblado de bytecode (`javap`), optimizaciones de rendimiento y mitigaciones de librerías de terceros (Google Play Core, AdMob). |
| **Blueprints & Frameworks** | `README.md`, `.agents/project_manifest.json` | Nuevas arquitecturas agénticas, bucles deterministas, routers de memoria RAG y reducciones porcentuales de consumo de tokens. |

---

## 3. Algoritmo de Traducción a Activos de Carrera

$$\text{Evidencia Técnica en Repositorio} \xrightarrow{\text{Lectura Inteligente}} \text{Métrica Cuantificable} \xrightarrow{\text{Humanizer}} \text{Bala de Alto Impacto (CV / LinkedIn)}$$

1. **Identificar:** Leer el artefacto de origen (ej. `RELEASE_NOTES_v1.0.0.md` en MascotIA).
2. **Contextualizar:** Extraer números, causas de fallos resueltos y decisiones de arquitectura.
3. **Traducir:** Convertir la evidencia en propuesta de valor para reclutadores técnicos (ej. *"Resolución de crash nativo en Android 14–17 mediante ingeniería forense en bytecode JVM"*).
4. **Sincronizar:** Replicar en PDF (ES/EN), LinkedIn, GitHub y Chuleta sin tocar una sola coma del código original del proyecto.
