# 22: Responder sobre Metagame sin agregados prohibidos

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Permitir consultas y Recommendations competitivas basadas únicamente en referencias oficiales vigentes del mismo entorno, absteniéndose cuando no exista evidencia aplicable.

**Blocked by:** 17: Consultar y mejorar un Deck con el Assistant; 21: Curar Competitive reference decks.

**Status:** ready-for-agent

- [ ] Una consulta de Metagame identifica o solicita periodo, región, Deck format, Card pool, reglas y baneos relevantes.
- [ ] Solo se recuperan Competitive reference decks del mismo Competitive environment.
- [ ] La respuesta atribuye presencia o resultado a su evento concreto sin inferir popularidad o superioridad general.
- [ ] Sin evidencia oficial vigente, el Assistant lo declara y limita el análisis a legalidad y sinergias verificables.
- [ ] Recommendations no prometen victorias, predicen porcentajes ni generan rankings propios.
- [ ] Cifras competitivas solo se repiten cuando una publicación oficial las expresa y siempre quedan atribuidas/acotadas.
- [ ] Tests cubren entorno coincidente, entorno distinto, ausencia de evidencia y prohibiciones estadísticas.
