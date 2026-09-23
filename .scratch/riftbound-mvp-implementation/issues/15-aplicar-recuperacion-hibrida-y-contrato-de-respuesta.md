# 15: Aplicar recuperación híbrida y contrato de respuesta

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Completar el contrato de respuestas de reglas con recuperación híbrida, Current rules state, abstención y tratamiento explícito de ambigüedad, conflictos y fallos.

**Blocked by:** 14: Responder una regla directa con fuente.

**Status:** ready-for-agent

- [ ] Full-text search por idioma y similitud vectorial se combinan mediante Reciprocal Rank Fusion en Postgres.
- [ ] Los candidatos se filtran por publicación activa, autoridad, vigencia, idioma, ámbito y tipo de fuente antes de generar.
- [ ] La precedencia respeta reglas explícitas, ámbito específico y versión inglesa autoritativa.
- [ ] El Assistant usa `needs_clarification`, `no_official_answer`, `official_conflict`, `missing_context` y `unavailable` cuando corresponda.
- [ ] Ningún estado no grounded improvisa hechos desde memoria general, foros o contenido comunitario.
- [ ] Las respuestas traducidas desde inglés lo indican y Facts permanecen separados de Recommendations.
- [ ] Tests cubren búsqueda híbrida, precedencia, vacío, conflicto, traducción y proveedor indisponible.
