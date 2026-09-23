# 14: Responder una regla directa con fuente

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Entregar el primer recorrido completo del Assistant: una pregunta directa sobre reglas obtiene una respuesta bilingüe breve y permite inspeccionar la Official rules source activa que la sustenta.

**Blocked by:** 13: Publicar y versionar conocimiento.

**Status:** ready-for-agent

- [ ] Ask permite formular una pregunta en español o inglés y muestra streaming o progreso accesible.
- [ ] El servidor recupera solo una Knowledge publication activa autorizada para el caso y no usa drafts o retiradas.
- [ ] OpenAI recibe únicamente los fragmentos mínimos recuperados y devuelve una salida estructurada validada.
- [ ] Una respuesta válida muestra estado `grounded`, texto breve y Facts separados.
- [ ] Las fuentes plegadas muestran título, enlace, fecha, idioma y fragmento relevante construido desde `source_ids` existentes.
- [ ] Un `source_id` inexistente, inactivo o no sustentador invalida la respuesta en vez de mostrarse.
- [ ] Tests verifican ambos idiomas, publicación activa, cita real y rechazo de cita inventada.
