# Chuleta Táctica para Entrevistas y Screenings Telefónicos (Blueprint)

> Última validación: 2026-09-03 | Estado: Plantilla Oficial Enterprise Hub  
> Respuestas rápidas estructuradas bajo metodología STAR, pitch de 60 segundos y preguntas de calibración técnica.

---

## 1. El Pitch de 60 Segundos (Elevator Pitch)

"Soy un Ingeniero de Sistemas e Inteligencia Artificial Aplicada centrado en software tolerante a fallos y auditoría de seguridad de modelos fundacionales. Cuento con experiencia evaluando más de 25 pipelines de LLMs en producción, asegurando que las respuestas sean veraces, resistentes a inyecciones de prompt y alineadas con normativas legales. Combino rigor en testing automatizado (100% pass rate) con agilidad en Python, Flutter y arquitecturas Cloud Serverless."

---

## 2. Respuestas Metodología STAR (Situación, Tarea, Acción, Resultado)

### STAR 1: Mitigación de Alucinaciones en un Pipeline de Producción
- **Situación:** Modelo fundacional generando datos médicos/legales no contrastados en casos límite.
- **Tarea:** Crear un arnés de evaluación factual automatizado con umbral $\ge 95\%$.
- **Acción:** Implementación de Router RAG jerárquico y compuerta de verificación contra fuentes canónicas.
- **Resultado:** Reducción del ratio de alucinación por debajo del 3% y eliminación de falsos positivos en producción.

### STAR 2: Optimización de Ventana de Contexto y Costes
- **Situación:** Sobrecarga de tokens (-80% de eficiencia) por escaneo indiscriminado de documentos.
- **Tarea:** Diseñar un enrutador semántico determinista de memoria modular.
- **Acción:** Creación de manifiestos estructurados con clasificación atómica de dominios bajo demanda.
- **Resultado:** Descenso drástico en el consumo de tokens y reducción de latencia en respuestas del agente.
