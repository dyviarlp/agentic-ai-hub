---
name: pocock-safety
description: Directrices de tipado estricto, contratos inmutables, serialización defensiva y seguridad en Dart 3.5+.
---

# Pocock Safety: Tipado Estricto y Contratos Inmutables (Dart 3.5+)

> **Nivel de Activación:** Nivel 0 (Fondo Inmutable - Siempre Activo).  
> **Objetivo:** Eliminar errores de tipo en tiempo de ejecución (`TypeError`, `NoSuchMethodError`), nulos descontrolados y mutaciones de estado accidentales.

---

## 1. Reglas Inmutables de Tipado en Dart

1. **Cero `dynamic` implícito o explícito:**
   - Prohibido usar `dynamic` como tipo de retorno o parámetro salvo en fronteras de deserialización JSON crudo.
   - En fronteras JSON, tipar inmediatamente como `Map<String, dynamic>` y validar tipos antes de instanciar entidades.
   - Prohibidos los casts forzados `as String` o `as int` sin verificación previa; usar `tryParse` o comprobaciones `is`.

2. **Inmutabilidad Absoluta en Capa de Dominio:**
   - Todo modelo de datos debe anotarse con `@immutable` o implementar campos `final` en su totalidad.
   - Todo modelo debe proveer constructores `const` y un método determinista `copyWith(...)`.
   - Prohibido mutar colecciones in-place (`list.add(...)`); usar colecciones inmutables o `List.unmodifiable(...)`.

3. **Pattern Matching Exhaustivo (Dart 3.x+):**
   - Usar `switch` expressions exhaustivas sobre `sealed classes` y `enums`.
   - Prohibido el uso de cláusulas `default` perezosas cuando se evalúen enums o estados cerrados; el compilador debe exigir el manejo de cada caso explícito.

4. **Contratos Defensivos en Serialización:**

   ```dart
   // Patrón oficial de deserialización segura
   factory MyEntity.fromMap(Map<String, dynamic> map) {
     return MyEntity(
       id: map['id']?.toString() ?? '',
       count: (map['count'] as num?)?.toInt() ?? 0,
       createdAt: DateTime.tryParse(map['createdAt']?.toString() ?? '') ?? DateTime.now(),
     );
   }
   ```
