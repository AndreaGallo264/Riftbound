# Definir la evaluación del asistente

Type: `grilling`
Status: `resolved`
Blocked by: 01, 04, 06, 07

## Question

¿Con qué conjunto de casos, métricas y umbrales se aceptarán respuestas sobre reglas, conflictos, colección, mazos y metajuego antes y durante la beta, incluyendo regresiones tras actualizar fuentes o cambiar el LLM?

## Answer

### Suite inicial

La beta comienza con 40 casos sintéticos y versionados, cada uno con input, contexto privado mínimo, Knowledge publication aplicable, respuesta/estado esperado, fuentes esperadas y rúbrica. No se utilizan conversaciones ni Collections reales de los testers.

- 10 casos de reglas directas;
- 6 de precedencia, FAQ, erratas o legalidad;
- 6 de abstención, conflicto oficial, ambigüedad o recuperación fallida;
- 6 de cálculos y consultas sobre Collection;
- 6 de Deck legality y Collection coverage;
- 4 de Recommendation y Metagame;
- 2 de aislamiento entre Beta testers.

Español, inglés, preguntas que requieren fuentes en el otro idioma y nombres oficiales de Cards se distribuyen entre todas las categorías en vez de formar un bloque separado.

### Evaluadores

- Checks deterministas validan schema, estados enumerados, IDs de fuentes existentes/activas, aislamiento de usuario, selección de tools y resultados calculables de Collection/Decks.
- Un LLM juez más capaz y fijado evalúa corrección semántica, apoyo real de las citas, calidad de abstención, equivalencia bilingüe y separación entre Facts y Recommendations.
- El juez recibe rúbrica, evidencia permitida y resultado esperado; devuelve un schema estructurado con puntuación, motivo y categorías de fallo.
- El juez no puede perdonar una invariante determinista fallida ni decidir que una fuente inexistente es válida.
- Los dos devs revisan cualquier bloqueo crítico o discrepancia llamativa antes de cambiar la suite, pero no inspeccionan manualmente cada respuesta aprobada.

### Barreras críticas

La ejecución bloquea apertura o cambio sensible si aparece cualquiera de estos casos:

- dato de otro Beta tester recuperado o expuesto;
- regla sin apoyo oficial presentada como cierta;
- cita inventada, inactiva o que no sustenta la afirmación;
- uso de una Knowledge publication retirada/sustituida como vigente;
- respuesta factual generada desde memoria del LLM tras fallar recuperación;
- schema inválido o cálculo determinista incorrecto.

Los casos críticos se ejecutan tres veces y cualquier repetición fallida bloquea. El resto se ejecuta una vez para controlar coste.

### Métricas y objetivos

- Cero barreras críticas abiertas.
- `100%` de schema válido, aislamiento, source IDs válidos y cálculos deterministas.
- Al menos `95%` de estado de respuesta correcto y recuperación de una fuente esperada entre los primeros cinco resultados cuando existe.
- Al menos `90%` de respuestas aprobadas por la rúbrica semántica del juez.
- Coste por caso, tokens, latencia p50/p95, tool elegido y causas de abstención se registran como tendencias, no como puertas hasta **Fijar los requisitos no funcionales del MVP**.

### Ejecución y versionado

La suite completa se ejecuta:

- antes de abrir la beta;
- al cambiar modelo generativo, embeddings, prompt de sistema, tools o schema;
- al cambiar retrieval, chunking o pipeline de ingestión;
- antes de publicar una actualización de reglas que afecte casos existentes;
- al corregir un incidente que deba convertirse en regresión.

Cada run conserva versión de suite, modelos, prompts, configuración de retrieval, pipeline, Knowledge publication, métricas, coste y latencia. Un cambio oficial actualiza solo casos afectados y conserva el historial de resultados anterior.

### Selección del modelo

Los candidatos se comparan sobre la misma suite y configuración. Se elige el modelo generativo más barato que cumpla todas las barreras y umbrales; una mejora de calidad que no cambia el resultado de aceptación no justifica por sí sola mayor coste. El modelo juez permanece fijado durante una comparación y cualquier cambio del juez inicia una nueva serie de resultados no mezclable con la anterior.

El feedback externo de los amigos durante la beta se triagea manualmente; un fallo reproducible añade o actualiza un caso antes de corregirse.
