---
name: cv-ats-optimizer
description: >-
  Optimiza la generación de currículums técnicos deterministas en exactamente 2 páginas A4 mediante Playwright, PyMuPDF y motores ATS. Controla presupuestos de espacio en milímetros, previene desbordamientos silenciosos y maximiza la densidad semántica de keywords para software engineering e IA.
---

# CV-ATS-Optimizer: Compilación Determinista y Optimización ATS

Esta skill garantiza que los CVs generados por código cumplan simultáneamente dos objetivos inflexibles:
1. Puntuación máxima en sistemas ATS (Applicant Tracking Systems).
2. Renderizado determinista en exactamente 2 páginas A4 sin desbordamientos visuales ni recortes silenciosos por CSS.

## 1. El Presupuesto Físico Inflexible (2 Páginas A4)

- **Dimensiones:** Exactamente 210mm x 297mm por página.
- **Paginación Estricta:** Uso de contenedores `.page` con `page-break-after: always;` y `break-after: page;`.
- **Detección de Desbordamiento Silencioso (Anti-Clipping):**
  - La presencia de `overflow: hidden` en CSS puede ocultar texto sin disparar una tercera página.
  - Es obligatorio auditar mediante script con `pymupdf` (`fitz`) que la última línea de texto de cada página esté efectivamente renderizada en el flujo textual del PDF.

## 2. Optimización Semántica para Parsers ATS

1. **Taxonomía Normalizada:** Emplear términos técnicos reconocidos por los parsers estándar (ej. *Clean Architecture, Riverpod, Playwright, Full-Stack, REST APIs, CI/CD, Kotlin/JVM Bytecode, Cloud Firestore*).
2. **Estructura Jerárquica Limpia:**
   - Nombre y datos de contacto en cabecera estándar.
   - Encabezados claros (`PERFIL PROFESIONAL`, `EXPERIENCIA LABORAL`, `PROYECTOS DESTACADOS`, `TECH STACK`, `EDUCACIÓN`, `CERTIFICACIONES`).
   - Sin tablas complejas de maquetación que distorsionen el orden de lectura en formato ATS puro.
3. **Compliance Estricto de Confidencialidad (NDA):**
   - Prohibido incluir nombres de clientes protegidos o herramientas propietarias internas de clientes en repositorios públicos o CVs.
   - Representar la experiencia a través del rol profesional (*AI QA & Algorithmic Safety Specialist*) y métricas genéricas (*29+ pipelines avalados, 100% de calidad*).
