# Memoria de Dominio 03: Gestión de Estado & Riverpod 3.x

> Última validación: 2026-09-02 | Estado: Plantilla Oficial Enterprise Hub  
> Invariantes de reactividad, providers desacoplados y ciclo de vida de estado.

---

## 📋 Reglas Preventivas de Dominio

1. **Gestores Exclusivos:** Uso de Riverpod 3.x con Notifier y AsyncNotifier. Prohibido el uso de ChangeNotifier o StateProvider legados.
2. **Manejo de Estados Asíncronos:** Toda llamada asíncrona debe ser modelada con AsyncValue y control exhaustivo de when(data, loading, error).
3. **Aislamiento de Lógica:** Prohibida la lógica de negocio dentro del árbol de widgets; delegar enteramente en providers y repositorios.
