# 20: Operar cuentas y soporte desde Admin

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Dar a los dos Admins las herramientas mínimas para operar invitaciones, estados de cuenta, soporte de datos y jobs sin permitir promoción de roles ni convertir datos privados en conocimiento.

**Blocked by:** 04: Aplicar ciclo de cuenta y aislamiento; 06: Gestionar Owned copies manualmente; 09: Crear y editar Decks borrador; 12: Ingerir una Knowledge source como draft; 18: Persistir y borrar Conversations.

**Status:** ready-for-agent

- [ ] El panel muestra invitaciones y estados básicos de cuentas sin permitir registro o promoción pública de Admins.
- [ ] Un Admin puede invitar, reenviar, revocar, suspender y reactivar mediante acciones explícitas.
- [ ] Un Admin puede inspeccionar Collection, Decks y Conversations para soporte y la UI comunica el carácter privado de esos datos.
- [ ] La inspección no ofrece una acción para promover datos privados a Knowledge source.
- [ ] El panel muestra estado, intentos y errores de jobs de ingestión sin exponer secretos.
- [ ] Un Beta tester no puede abrir rutas ni ejecutar operaciones Admin manipulando cliente o peticiones.
- [ ] Tests cubren permisos, operaciones de cuenta, inspección y prohibiciones editoriales.
