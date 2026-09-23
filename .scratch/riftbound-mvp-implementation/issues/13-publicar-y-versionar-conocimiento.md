# 13: Publicar y versionar conocimiento

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Permitir que un Admin revise, corrija fidelidad técnica y active una Knowledge revision junto con su índice, conservando historial y una última publicación válida ante fallos.

**Blocked by:** 12: Ingerir una Knowledge source como draft.

**Status:** ready-for-agent

- [ ] La revisión muestra metadatos, fragmentos, diferencias y relaciones de precedencia/sustitución antes de aprobar.
- [ ] Las correcciones crean datos revisionados y se limitan a extracción, segmentación, metadatos o traducción fiel.
- [ ] Aprobar activa Knowledge publication, revisión y artefactos de recuperación en una transacción corta y atómica.
- [ ] Una publicación nueva marca la anterior `superseded`; retirar marca la activa `withdrawn`.
- [ ] Un rollback crea una nueva Knowledge publication con actor, instante y motivo, sin reactivar silenciosamente la anterior.
- [ ] Un fallo de embeddings, validación o activación conserva la última publicación válida.
- [ ] Tests prueban publicación, sustitución, retirada, rollback, auditoría y fallo sin estado parcial.
