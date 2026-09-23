# 05: Explorar Cards y Printings

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Permitir explorar un Card catalog de prueba autorizado y distinguir identidad jugable, revisión y publicación física, dejando una frontera clara para sustituir la fuente sin cambiar la experiencia.

**Blocked by:** 02: Desplegar la shell bilingüe responsive.

**Status:** ready-for-agent

- [ ] El catálogo representa Card, Card revision y Printing como conceptos separados y conserva la vigencia de revisiones.
- [ ] Un usuario puede buscar por nombre oficial, identificador o número de coleccionista y filtrar resultados básicos.
- [ ] El detalle de una Card muestra sus datos jugables actuales y las Printings disponibles sin confundirlas.
- [ ] Los datos iniciales pueden derivarse localmente de `slimtreble/Riftbound-card-data`, registrando commit y procedencia y sin incluir artwork.
- [ ] La UI y los tests dejan claro que el dataset comunitario es un fixture reemplazable, no una fuente autorizada de producción ni de erratas vigentes.
- [ ] La aplicación accede al catálogo mediante un contrato propio que no expone el formato de un proveedor concreto al dominio.
- [ ] Los estados vacío, carga, error y ausencia de coincidencias son accesibles y bilingües.
- [ ] Tests verifican búsqueda, resolución Card/Printing y selección de la Card revision vigente.
