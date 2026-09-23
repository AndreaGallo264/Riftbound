# 07: Exportar y reimportar identidades de Collection

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Dar al tester un CSV documentado que preserve las identidades de sus Owned copies y pueda volver a aplicarse para actualizar esas copias sin duplicarlas.

**Blocked by:** 06: Gestionar Owned copies manualmente.

**Status:** ready-for-agent

- [ ] La exportación incluye IDs estables, Card/Printing y todos los atributos editables de cada Owned copy.
- [ ] El archivo usa una plantilla versionada, documentada y compatible con caracteres españoles e ingleses.
- [ ] Volver a cargar filas con IDs propios actualiza las copias correspondientes en lugar de crear duplicados.
- [ ] IDs inexistentes, ajenos o repetidos se rechazan y no permiten modificar datos de otro tester.
- [ ] Antes de aplicar una reimportación se muestra un resumen de las copias que cambiarán.
- [ ] Un fallo de validación no deja actualizaciones parciales.
- [ ] Un test round-trip demuestra que exportar y reimportar conserva identidad y atributos.
