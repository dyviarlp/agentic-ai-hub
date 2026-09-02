# Memoria de Dominio 01: Core Logic & Inmutabilidad

> Ãšltima validaciÃ³n: 2026-09-02 | Estado: Plantilla Oficial Enterprise Hub  
> Invariantes de capa de dominio, serializaciÃ³n a prueba de nulos y tipado estricto.

---

## ðŸ“‹ Reglas Preventivas de Dominio

1. **Inmutabilidad Absoluta:** Toda clase de dominio debe ser inmutable (`final`), anotada con `@immutable` y con constructor `const`.
2. **SerializaciÃ³n Segura:** Mapear colecciones nulas a listas vacÃ­as `?? const []` para evitar `TypeError`.
3. **Pattern Matching Exhaustivo:** `switch` expressions sobre enums o clases selladas sin clausula `default` perezosa.
