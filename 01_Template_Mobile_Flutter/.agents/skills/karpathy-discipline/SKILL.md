---
name: karpathy-discipline
description: Disciplina de ingeniería empírica, diagnóstico forense CLI y modo Urgency Bypass para hotfixes.
---

# Karpathy Discipline: Ingeniería Empírica y Diagnóstico Forense

> **Nivel de Activación:** Nivel 2 (Modo de Operación para `fix:` y `hotfix:`).  
> **Objetivo:** Erradicar las conjeturas por similitud de nombres y resolver bugs de raíz mediante evidencia reproducible.

---

## 1. Los 4 Principios de Disciplina

1. **Pensar antes de codificar (Explicitar la interpretación):**
   - Antes de abrir un editor, declarar por escrito: qué falló, cuál es la hipótesis causal y qué comando confirmará o refutará la hipótesis.
2. **Cero Conjeturas por Similitud Semántica:**
   - Queda terminantemente prohibido asumir la causa de un crash porque una palabra del error coincida con el nombre de un archivo del proyecto.
   - En crashes de dependencias o nativos (Android/iOS), inspeccionar empíricamente el árbol de dependencias (`./gradlew dependencyInsight`) o el bytecode antes de tocar código Dart.
3. **Edición Quirúrgica de Mínimo Impacto:**
   - Atacar la causa raíz exacta. Prohibido refactorizar archivos no relacionados durante la resolución de un bug.
4. **Verificación contra Objetivos Explícitos:**
   - La tarea solo se da por cerrada cuando un comando determinista (test, análisis o inspección de artefacto) demuestre que el síntoma desapareció.

---

## 2. Protocolo "Urgency Bypass" (Para Hotfixes y Crashes en Producción)

Cuando la tarea sea un `hotfix:` o corrección de crash crítico en producción:

- **Salto de Burocracia:** Se omite la redacción de planes extensos o diseño de alternativas; el agente entra directamente en modo **Forense CLI ➔ Parche Quirúrgico ➔ Verificación de Gates**.
- **Comprobación de Manifiesto y Artefacto:** Si el parche afecta configuraciones de compilación o manifiestos nativos, verificar el manifiesto ensamblado (`processReleaseManifest`) antes de dar el fix por válido.
