# 21: Curar Competitive reference decks

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Permitir que un Admin registre decklists y observaciones oficiales con su Competitive environment, retirándolas de la vigencia cuando cambien sus condiciones sin derivar estadísticas agregadas.

**Blocked by:** 10: Calcular Deck legality y Collection coverage; 13: Publicar y versionar conocimiento.

**Status:** ready-for-agent

- [ ] Solo publicaciones y decklists oficiales autorizadas pueden convertirse en Competitive reference deck.
- [ ] Cada referencia conserva fuente, evento, fecha, región, Deck format, Card pool, reglas y baneos aplicables.
- [ ] La copia o retención de contenido respeta el permiso registrado; en su ausencia solo se guardan metadatos y enlaces permitidos.
- [ ] Cambiar set, legalidad, ban, reglas o formato impide considerar vigente una referencia del entorno anterior.
- [ ] No se calculan ni almacenan rankings, play rates, win rates, conversiones o porcentajes de matchup.
- [ ] La UI Admin muestra vigencia y razón de obsolescencia sin borrar contexto histórico permitido.
- [ ] Tests cubren entorno equivalente, invalidación por cambios y ausencia de agregados prohibidos.
