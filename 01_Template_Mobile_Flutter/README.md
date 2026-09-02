# 📱 Template 01: Mobile Flutter Enterprise Hub (2026)

> **Specialty:** Lead Mobile Engineer & Flutter Architect  
> **Author:** Juan Armando Rodríguez Pérez  
> **Target OS:** Android API 34–37 (Android 15/16/17 Ready), iOS 17+  
> **State Engine:** Riverpod 3.x (`Notifier` / `AsyncNotifier`)  
> **Architecture:** Clean Architecture, Domain Router RAG & Lifecycle Skills  
> **Paradigm:** In-Memory Safe Storage, 360° Reactive Loop & Shift-Left QA

---

## 🏛️ Architecture & Enterprise Framework

This blueprint implements the **Enterprise Mobile Agent Core**, engineered after rigorous cross-model Red Teaming:

1. **Decoupled Project Contract (`project_manifest.json`):**
   - Agnostic configuration for test runners, linters, release builds, and active memory domains.
   - Dynamic test discovery (`flutter test` live evaluation, zero hardcoded counts).
2. **System Prompt Anchor (<600 tokens):**
   - Fixed baseline: Clean Architecture layers (`models` ➔ `repositories` ➔ `providers` ➔ `screens`).
   - Riverpod 3.x inmutability with mandatory `ref.onDispose` cleanup.
   - **End-to-End Reactive Loop (Bucle 360°):** Every state mutation automatically connects and synchronizes local storage, alarms, notifications, and Crashlytics.
3. **Lifecycle Skills Hierarchy (Zero Collisions):**
   - **Level 0 (Immutable Base):** `pocock-safety` — Strict Dart 3.5+ typing, zero forced casts, immutable models.
   - **Level 1 (Phase 2 Planning Only):** `ponytail` — YAGNI decision ladder and minimum Git diff metric (auto-deactivates in Phase 3 Execution).
   - **Level 2 (Operational Mode):** `karpathy-discipline` — CLI forensic diagnosis (`dependencyInsight`, bytecode, logs) and *Urgency Bypass* for `fix:` and `hotfix:`.
4. **Hierarchical Domain-Router RAG:**
   - Multi-domain on-demand retrieval (max 1-3 domain files loaded per task).
   - *Session-scope* caching to prevent token bloat and redundant re-reads.
   - External blocker short-circuit (immediate escalation for platform/keystore blocks vs automatic fallback for transient services).

---

## 🚀 1-Minute Drop-In Activation

To activate this agent template in any new Flutter project:

1. Copy `.agents/` into your Flutter workspace root:
   ```bash
   cp -r 01_Template_Mobile_Flutter/.agents /path/to/my-new-flutter-app/
   ```
2. Edit `.agents/project_manifest.json` with your app name and commands.
3. Open Antigravity / your agent IDE — it will automatically detect `.agents/AGENTS.md` and operate with senior enterprise discipline.
