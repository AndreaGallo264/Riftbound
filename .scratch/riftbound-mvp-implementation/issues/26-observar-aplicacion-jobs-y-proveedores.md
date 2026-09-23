# 26: Observar aplicación, jobs y proveedores

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Proporcionar señales operativas correlacionadas para diagnosticar peticiones, jobs, proveedores y costes sin registrar contenido privado completo ni secretos.

**Blocked by:** 13: Publicar y versionar conocimiento; 15: Aplicar recuperación híbrida y contrato de respuesta.

**Status:** ready-for-agent

- [ ] Se registran errores, estados/reintentos de jobs, disponibilidad de proveedor, latencias, tokens, costes y cuotas.
- [ ] Request, tester seudonimizado, run LLM, job y Knowledge publication pueden correlacionarse mediante IDs técnicos.
- [ ] Logs y trazas excluyen prompts, respuestas, Conversations, Collection y Decks completos, además de secretos.
- [ ] Se miden p50/p95 para páginas, Collection/Deck, primer token, respuesta completa y jobs sin convertirlos todavía en SLA.
- [ ] Existen alertas para presupuesto, fallos repetidos de ingestión, incremento de errores Auth/RLS y proveedor LLM indisponible.
- [ ] Logs y trazas operativas expiran a los 14 días.
- [ ] Tests o comprobaciones automatizadas demuestran redacción de secretos y datos privados representativos.
