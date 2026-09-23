# 11: Importar y exportar Decks

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Permitir trasladar un Deck mediante texto simple o CSV propio, con una previsualización que resuelva formato, secciones y Cards ambiguas antes de escribir.

**Blocked by:** 09: Crear y editar Decks borrador; 10: Calcular Deck legality y Collection coverage.

**Status:** ready-for-agent

- [ ] Un tester puede pegar una lista de texto o cargar el CSV propio para iniciar una importación.
- [ ] La previsualización muestra Deck format, secciones, cantidades, Cards resueltas, ambigüedades y errores.
- [ ] Las ambigüedades requieren selección explícita o descarte y nunca se resuelven silenciosamente.
- [ ] Confirmar crea o actualiza el Deck como una única operación y vuelve a calcular legalidad y cobertura.
- [ ] Cada Deck se exporta como texto y CSV conservando formato, secciones y cantidades.
- [ ] Cancelar o fallar una importación no altera el Deck existente.
- [ ] Tests round-trip cubren texto, CSV, ambigüedad y error atómico.
