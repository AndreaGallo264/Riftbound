# 17: Consultar y mejorar un Deck con el Assistant

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Permitir preguntar por un Deck concreto y recibir explicaciones deterministas y Recommendations separadas, incluida una opción limitada a Collection y otra ideal con faltantes.

**Blocked by:** 10: Calcular Deck legality y Collection coverage; 15: Aplicar recuperación híbrida y contrato de respuesta; 16: Consultar la Collection con el Assistant.

**Status:** ready-for-agent

- [ ] Collection o Deck pueden abrir un Assistant lateral en escritorio y a pantalla completa en móvil sin perder contexto.
- [ ] El compositor identifica nombre y versión actual del Deck usado en cada pregunta.
- [ ] El Assistant explica Deck legality y Collection coverage usando los cálculos deterministas, no inferencias del LLM.
- [ ] Facts y Recommendations aparecen separados y las sugerencias explican reglas y sinergias utilizadas.
- [ ] Cuando resulte útil se ofrecen una propuesta limitada a Cards poseídas y otra ideal con Cards/cantidades faltantes.
- [ ] Las propuestas son estructuradas pero nunca modifican el Deck automáticamente.
- [ ] Tests cubren Deck fresco, cambio durante Conversation, faltantes, formato ambiguo y ausencia de permisos.
