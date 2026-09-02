---
name: ponytail
description: Sesgo de extrema simplicidad (YAGNI) y minimización de diffs para diseño y planificación en Flutter/Dart.
---

# Ponytail: La Escalera YAGNI y Simplicidad Radical

> **Nivel de Activación:** Nivel 1 (Fase de Diseño / Planning únicamente).  
> **Ámbito Estricto:** Activo EXCLUSIVAMENTE durante la Fase 2 (Torneo de Opciones).  
> **⚠️ Condición de Apagado Inmutable:** En Fase 3 (Ejecución y Cierre de Bucle 360°), Ponytail se DESACTIVA. Nunca puede recortar la actualización de Providers, persistencia en Storage o cancelación de alarmas.

---

## 1. La Escalera de Decisión YAGNI para Flutter

Antes de proponer escribir una sola línea de código nuevo, el agente debe subir esta escalera:

1. **¿Tiene que existir realmente?** ¿Resuelve el problema o es anticipación de una necesidad hipotética futura? Si es hipotética, descartar.
2. **¿Ya existe en el proyecto?** Buscar antes en `lib/widgets/`, `lib/services/` y `lib/models/`. Reutilizar componentes consolidados.
3. **¿Lo resuelve el SDK estándar de Flutter/Dart?** Usar widgets nativos (`LayoutBuilder`, `ListView.builder`, `SingleChildScrollView`, `AnimatedCrossFade`) antes de añadir paquetes o inventar widgets complejos.
4. **¿Hay una dependencia ya instalada que lo resuelva?** Consultar `pubspec.yaml` antes de importar nuevas librerías.
5. **¿Puede resolverse en 5-10 líneas limpias?** Rechazar arquitecturas de 5 clases abstractas para resolver una transformación de datos simple.
6. **Métrica del Git Diff Mínimo:** La mejor solución es la que resuelve el requerimiento con el menor número de líneas modificadas y cero riesgo de regresión.

---

## 2. Límites y Subordinación al Bucle 360°

- **Prohibido el "YAGNI destructivo":** Ponytail jamás podrá usarse como excusa para omitir `ref.onDispose()`, dejar alarmas locales huérfanas o no envolver llamadas remotas en bloques `try/catch` con telemetría Crashlytics.
- La simplicidad de Ponytail aplica a la **solución de diseño**, nunca a la omisión de las compuertas de calidad.
