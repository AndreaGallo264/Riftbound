# Fijar la autoridad, vigencia y resolución de conflictos entre fuentes

Type: `grilling`
Status: `resolved`
Blocked by: 02

## Question

¿Qué jerarquía editorial, reglas de vigencia y tratamiento de contradicciones debe aplicar el producto entre reglas oficiales, rulings, foros oficiales y contenido comunitario, y cómo debe mostrárselo al usuario?

## Answer

### Fuentes admitidas para reglas

El Assistant solo presenta como reglas las **Official rules sources** publicadas por Riot: Rules Hub, Core Rules, Tournament Rules, FAQ/rulings, patch notes, erratas, avisos de legalidad y addenda oficiales de eventos.

- Se excluyen como autoridad de reglas los foros, incluso publicaciones de personal o jueces identificados, y todo contenido comunitario.
- Un Admin no puede promover una interpretación comunitaria o propia a regla oficial.
- El contenido comunitario puede seguir usándose, con su naturaleza no oficial visible, para listas y análisis competitivos conforme a las restricciones de licencia; no resuelve reglas.

### Precedencia y vigencia

- El MVP responde únicamente sobre el **Current rules state**; no reconstruye estados históricos.
- Se aplica primero cualquier relación explícita de precedencia, ámbito o sustitución declarada por Riot.
- Dentro de su ámbito, una fuente oficial específica prevalece sobre una general: por ejemplo, un addendum del evento sobre Tournament Rules y Tournament Rules sobre Core Rules para competición.
- FAQ, patch notes y erratas prevalecen cuando la propia publicación así lo declara, hasta que una fuente posterior las incorpore o sustituya.
- La versión inglesa prevalece siempre ante discrepancias con una traducción. El Assistant puede responder en español, pero debe conservar el significado de la fuente inglesa y advertir que tradujo la respuesta.
- Cada afirmación conserva internamente fuente, URL, fecha de publicación/actualización, fecha de consulta, idioma, ámbito y relaciones de sustitución o precedencia, aunque esos datos no se desplieguen por defecto.

### Conflictos y ausencia de respuesta

- Si dos fuentes oficiales vigentes parecen contradecirse y Riot no declara cuál prevalece, el Assistant no elige: declara que no existe una respuesta oficial inequívoca.
- Si ninguna fuente oficial vigente cubre el caso, responde que no se sabe oficialmente; no completa el vacío con consenso, memoria del modelo ni una regla local del Admin.
- Las fuentes se muestran bajo demanda. Como mínimo se ofrece título, enlace, fecha, idioma y el fragmento que fundamenta la respuesta o el conflicto.
- Una respuesta nunca puede citar una fuente que no sustente realmente la afirmación.

La presentación exacta de estas respuestas y del acceso a sus fuentes se concreta en **Definir el contrato de respuesta del asistente**. La incorporación, revisión y retirada de documentos se concreta en **Definir el ciclo de vida del conocimiento**.
