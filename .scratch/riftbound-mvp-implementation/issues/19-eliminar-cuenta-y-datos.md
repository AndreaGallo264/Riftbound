# 19: Eliminar una cuenta y sus datos

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Permitir que un tester exporte sus datos y elimine irreversiblemente cuenta, Collection, Decks y Conversations activas mediante un recorrido autoservicio seguro.

**Blocked by:** 07: Exportar y reimportar identidades de Collection; 11: Importar y exportar Decks; 18: Persistir y borrar Conversations.

**Status:** ready-for-agent

- [ ] La interfaz ofrece exportaciones de Collection y Decks antes de iniciar el borrado.
- [ ] El borrado exige reautenticación o confirmación inequívoca y explica su irreversibilidad y la ventana de backups.
- [ ] Confirmar revoca sesiones y elimina datos activos de cuenta, Collection, Decks y Conversations como una operación controlada.
- [ ] Los datos borrados dejan de estar disponibles inmediatamente para UI, Admin support y Assistant.
- [ ] Solo permanecen tombstones técnicos mínimos permitidos y nunca contienen material disponible al Assistant.
- [ ] Repetir una solicitud completada es idempotente y no recrea la identidad.
- [ ] Tests automatizados verifican cascada, revocación, ausencia activa y rechazo posterior de acceso.
