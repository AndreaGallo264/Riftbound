# 10: Calcular Deck legality y Collection coverage

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Mostrar por separado si un Deck cumple su formato y qué Cards faltan respecto de la Collection, de forma determinista y actualizada tras cada cambio.

**Blocked by:** 06: Gestionar Owned copies manualmente; 09: Crear y editar Decks borrador.

**Status:** ready-for-agent

- [ ] Deck legality valida composición, secciones, cantidades, Card pool, reglas y baneos disponibles sin llamar al LLM.
- [ ] La interfaz distingue errores confirmados de casos no validables por falta de datos oficiales.
- [ ] Collection coverage compara cantidades de Card requeridas y Owned copies disponibles sin exigir Printing concreta.
- [ ] La cobertura no cambia la legalidad y una misma copia puede contar para varios Decks independientes.
- [ ] Editar o eliminar Owned copies recalcula faltantes sin modificar entradas del Deck.
- [ ] Cada resultado puede explicarse mediante los datos y reglas deterministas que lo produjeron.
- [ ] Tests cubren formatos, secciones, faltantes, copias compartidas y separación legalidad/cobertura.
