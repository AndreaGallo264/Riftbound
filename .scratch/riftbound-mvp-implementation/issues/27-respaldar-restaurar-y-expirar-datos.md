# 27: Respaldar, restaurar y expirar datos

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Cumplir los objetivos de recuperación y retención con un backup lógico cifrado separado y un procedimiento de restauración probado, incluida la expiración de datos borrados.

**Blocked by:** 19: Eliminar una cuenta y sus datos.

**Status:** ready-for-agent

- [ ] Un proceso diario crea un backup lógico cifrado fuera del Postgres primario y conserva siete días.
- [ ] El procedimiento documentado permite restaurar aplicación y datos con objetivos `RPO <= 24 h` y `RTO <= 24 h`.
- [ ] Una restauración de prueba completa verifica cuentas, Collection, Decks, Conversations y publicaciones sin exponer secretos.
- [ ] Datos eliminados desaparecen de backups al rotar en un máximo de siete días.
- [ ] Knowledge revisions y auditoría se conservan mientras el permiso lo permita; una obligación de borrado prevalece y deja solo tombstone permitido.
- [ ] Fallos de backup o restauración generan una alerta visible para los desarrolladores.
- [ ] La prueba puede repetirse tras cambios relevantes de esquema o mecanismo de backup.
