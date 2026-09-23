# Definir el contrato de respuesta del asistente

Type: `grilling`
Status: `resolved`
Blocked by: 01, 03, 04

## Question

¿Qué debe incluir una respuesta sobre reglas, colección o mazos en cada idioma, cómo cita evidencia y contexto del usuario, y cuándo debe declarar incertidumbre, conflicto, falta de datos o imposibilidad de responder?

## Answer

### Forma común

- El Assistant responde en el idioma de la pregunta, salvo que el usuario pida otro. Conserva los nombres oficiales de las Cards y avisa cuando traduce contenido oficial inglés.
- Presenta primero una respuesta breve y directa; después, explicación, límites y recomendaciones relevantes.
- Las fuentes no se despliegan por defecto, pero siempre están disponibles bajo demanda.
- Si una ambigüedad sobre Card, Deck, Deck format o contexto puede cambiar la respuesta, pide aclaración antes de responder.
- Distingue visual y semánticamente hechos, reglas y Recommendations.

### Contexto y frescura

- Una consulta de inventario puede usar la Collection completa del Beta tester.
- Una consulta de mazo usa únicamente el Deck activo o nombrado; la respuesta identifica qué Deck empleó.
- En cada petición se consulta el último estado guardado, aunque la Collection o el Deck hayan cambiado durante la conversación.
- Nunca accede a Collections o Decks de otro usuario ni mezcla sus datos en una respuesta.
- Para hechos de colección o mazo, el dato privado utilizado ocupa el lugar de la evidencia y debe poder identificarse por entidad y versión o instante de lectura.

### Respuestas de reglas

- Una Grounded answer sobre reglas solo usa el Current rules state procedente de Official rules sources.
- Al solicitar fuentes, el usuario recibe título, enlace, fecha de actualización, idioma y fragmento relevante. La versión inglesa es autoritativa.
- La memoria general del LLM, foros y contenido comunitario no pueden completar una regla ausente ni sustituir una recuperación fallida.

### Estados explícitos

El Assistant no muestra porcentajes de confianza inventados. Usa uno de estos resultados reconocibles cuando corresponda:

- `grounded`: existe evidencia suficiente y recuperada;
- `needs_clarification`: falta una decisión del usuario que cambia la respuesta;
- `no_official_answer`: ninguna fuente oficial vigente resuelve la regla;
- `official_conflict`: fuentes oficiales vigentes discrepan sin precedencia resuelta;
- `missing_context`: falta Collection, Deck, Deck format u otro dato privado necesario;
- `unavailable`: falló la recuperación o un servicio requerido.

En cualquier estado distinto de `grounded`, explica brevemente qué falta o falló y no improvisa una respuesta factual.

### Recomendaciones

- Los consejos sobre Decks o Collection aparecen separados y etiquetados como Recommendation.
- Explican la evidencia y el contexto usados, distinguen Cards poseídas y faltantes, y pueden proponer Cards no poseídas.
- Nunca presentan preferencia, popularidad o análisis competitivo como una regla oficial.
- Los límites específicos de evidencia de Metagame se fijan en **Delimitar el metajuego y las recomendaciones de mazos**.

Este contrato define contenido y comportamiento, no la presentación visual, que se validará en **Prototipar la experiencia bilingüe de colección y consultas**.
