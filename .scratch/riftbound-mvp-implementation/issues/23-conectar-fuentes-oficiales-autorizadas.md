# 23: Conectar fuentes autorizadas de producción

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Sustituir los fixtures locales por fuentes de catálogo y conocimiento cuya licencia o autorización permita el uso de producción, conservando procedencia, versiones y una degradación segura ante cambios externos.

**Blocked by:** 01: Confirmar derechos de datos para producción; 05: Explorar Cards y Printings; 13: Publicar y versionar conocimiento; 21: Curar Competitive reference decks.

**Status:** ready-for-agent

- [ ] La integración aplica exactamente los usos, retención, atribución y límites documentados por la fuente autorizada.
- [ ] La fuente autorizada alimenta el adaptador de catálogo sin acoplar el dominio a su formato; el MVP no depende de `riftbound-content-v1`.
- [ ] Versiones, fechas de actualización, idioma, URL, fecha de consulta y hash se conservan para cada dato o fuente aplicable.
- [ ] Rules Hub y cualquier documento cuyo uso esté autorizado entran por el ciclo draft/revisión/publicación, nunca se publican automáticamente.
- [ ] La sincronización es idempotente y un fallo conserva catálogo/publicación válidos anteriores con estado visible.
- [ ] La integración no despliega `slimtreble/Riftbound-card-data`, artwork, endpoints, scraping o contenido que la licencia/autorización no cubra.
- [ ] Tests de contrato con fixtures grabados autorizados cubren actualización, retirada, error y cambio de esquema.
