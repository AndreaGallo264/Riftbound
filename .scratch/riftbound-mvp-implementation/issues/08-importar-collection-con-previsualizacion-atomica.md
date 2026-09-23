# 08: Importar Collection con previsualización atómica

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Permitir importar hasta 10.000 filas de la plantilla propia, resolver coincidencias dudosas y confirmar un resultado completo en modo `append` o `replace` sin cambios parciales.

**Blocked by:** 06: Gestionar Owned copies manualmente.

**Status:** ready-for-agent

- [ ] Se aceptan CSV de hasta 10 MB y 10.000 filas y se rechazan límites superiores antes de procesar.
- [ ] La previsualización separa altas, actualizaciones, eliminaciones, advertencias y errores.
- [ ] Coincidencias ambiguas o inexistentes exigen elegir Card/Printing o descartar la fila.
- [ ] `append` añade las copias confirmadas sin sustituir la Collection existente.
- [ ] `replace` muestra las eliminaciones y sustituye la Collection solo tras confirmación explícita.
- [ ] Confirmar aplica toda la previsualización en una transacción o no aplica nada.
- [ ] Tests cubren ambos modos, ambigüedad, límites, cancelación y rollback ante error.
