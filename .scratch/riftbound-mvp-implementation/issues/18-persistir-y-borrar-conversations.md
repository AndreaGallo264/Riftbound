# 18: Persistir y borrar Conversations

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Conservar el historial del Assistant por tester para continuar consultas y permitir borrar una Conversation o todo el historial sin afectar conocimiento compartido.

**Blocked by:** 04: Aplicar ciclo de cuenta y aislamiento; 15: Aplicar recuperación híbrida y contrato de respuesta.

**Status:** ready-for-agent

- [ ] Una pregunta crea o continúa una Conversation privada asociada al tester autenticado.
- [ ] Mensajes y metadatos necesarios se conservan en Postgres, no en almacenamiento propietario del proveedor como registro principal.
- [ ] El usuario puede listar, renombrar o reabrir sus Conversations sin acceder a las de otro tester.
- [ ] Se puede borrar una Conversation concreta o todas mediante confirmación explícita.
- [ ] Borrar historial no elimina Knowledge sources ni incorpora contenido privado al corpus compartido.
- [ ] Logs y trazas no contienen el texto completo de mensajes o respuestas.
- [ ] Tests prueban persistencia, aislamiento, continuidad y ambos niveles de borrado.
