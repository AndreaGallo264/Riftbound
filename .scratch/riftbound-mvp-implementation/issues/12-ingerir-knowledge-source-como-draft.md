# 12: Ingerir una Knowledge source como draft

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Permitir que un Admin cargue una URL o archivo autorizado y obtenga una Knowledge revision inmutable en draft, con extracción, metadatos y errores visibles sin afectar conocimiento publicado.

**Blocked by:** 02: Desplegar la shell bilingüe responsive; 04: Aplicar ciclo de cuenta y aislamiento.

**Status:** ready-for-agent

- [ ] Solo un Admin puede registrar una URL o subir un archivo a almacenamiento privado.
- [ ] Se validan tipo, tamaño máximo de 25 MB, hasta 300 páginas, hash, procedencia e identidad de fuente antes de procesar.
- [ ] Trigger.dev ejecuta etapas idempotentes y reintentables para extracción y fragmentación.
- [ ] La Knowledge revision draft conserva fuente, URL, idioma, fechas, hash, versión de pipeline, posiciones/páginas y errores.
- [ ] Repetir el mismo job no duplica revisiones ni fragmentos y cada intento queda trazable.
- [ ] La UI Admin muestra progreso, fallo y resultado revisable, pero ningún draft aparece en consultas públicas.
- [ ] Tests cubren autorización, validación, reintento, idempotencia y exclusión de drafts.
