# Memoria de Dominio 01: Core Logic & Inmutabilidad

> Última validación: 2026-09-02 | Estado: Plantilla Oficial Enterprise Hub  
> Invariantes de capa de dominio, serialización a prueba de nulos y tipado estricto.

---

## 📋 Reglas Preventivas de Dominio

1. **Inmutabilidad Absoluta:** Toda clase de dominio debe ser inmutable (inal), anotada con @immutable y con constructor const.
2. **Serialización Segura:** Mapear colecciones nulas a listas vacías ?? const [] para evitar TypeError.
3. **Pattern Matching Exhaustivo:** switch expressions sobre enums o clases selladas sin cláusula default perezosa.
