# 📱 Template 01: Mobile Flutter Full-Stack (2026)

> **Specialty:** Lead Mobile Engineer & Flutter Architect  
> **Target OS:** Android API 34–37 (Android 15/16/17 Ready), iOS 17+  
> **State Engine:** Riverpod 3.x (`Notifier` / `AsyncNotifier`)  
> **Native MCPs:** `firebase`, `google_maps_platform`, `flutter/dart`, `github`  
> **Paradigm:** Clean Architecture, In-Memory Safe Storage & Shift-Left QA

---

## 🏛️ Architecture Principles

1. **Clean Layer Separation:**
   - `lib/models/`: Immutable records/classes with `copyWith`, `fromJson`, `toJson`.
   - `lib/providers/`: Riverpod 3.x Notifiers. Zero legacy StateNotifier.
   - `lib/repositories/`: Data persistence, cache-first strategies, and remote bridges.
   - `lib/screens/` & `lib/widgets/`: Defensive UI, `SafeArea` wrappers, `const` constructors.
2. **Defensive Media Pipeline:**
   - Pre-upload image compression (800px max width, JPEG 75%, <80KB target).
   - In-memory `putData(bytes)` uploads to prevent local storage leaks.
3. **Zero Secrets in Source:**
   - All API keys read dynamically via `Env` (`lib/env/env.dart`) mapping `.env`.
4. **Shift-Left Automated QA:**
   - 0 errors in `flutter analyze`.
   - 100% passing tests in `flutter test`.

---

## 🚀 Drop-In Activation

To activate this agent template in any Flutter repository:
```bash
cp -r .agents /path/to/your-flutter-project/
```
