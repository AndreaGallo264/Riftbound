# 09: Crear y editar Decks borrador

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Permitir que un tester construya y conserve Decks propios por formato y secciones, incluso cuando estén incompletos, sean ilegales o contengan Cards no poseídas.

**Blocked by:** 04: Aplicar ciclo de cuenta y aislamiento; 05: Explorar Cards y Printings.

**Status:** ready-for-agent

- [ ] Se puede crear, renombrar, duplicar y eliminar un Deck privado.
- [ ] Cada Deck declara Deck format y organiza entradas Card más cantidad por Deck sections válidas para ese formato.
- [ ] Se pueden añadir, quitar, mover y ajustar cantidades mediante controles explícitos.
- [ ] Un Deck incompleto, ilegal o con Cards no poseídas puede guardarse y volver a editarse.
- [ ] Cambiar Deck format conserva entradas y secciones recuperables en lugar de eliminar Cards silenciosamente.
- [ ] La vista densa funciona en escritorio y se adapta a móvil sin ocultar acciones críticas.
- [ ] Tests verifican CRUD, aislamiento, duplicado y cambio de formato sin pérdida.
