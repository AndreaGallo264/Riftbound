# Definir los recorridos y el éxito del MVP

Type: `grilling`
Status: `resolved`

## Question

¿Qué recorridos completos deben poder realizar los usuarios y admins de la beta, y qué resultados observables demostrarán que el MVP cumple su promesa sin incluir capacidades posteriores?

## Answer

El MVP validará conjuntamente que los jugadores pueden mantener datos propios útiles y recibir respuestas fiables basadas en ellos y en conocimiento trazable.

### Recorridos del beta tester

1. **Colección**: entrar mediante invitación, buscar y ajustar cartas manualmente o importar una lista/archivo estructurado, corregir incidencias y consultar el resultado guardado.
2. **Mazo**: crear o importar un mazo, guardarlo, comprobar legalidad y cartas faltantes respecto de la Collection, y consultar al Assistant sobre sus reglas, composición y posibles mejoras.
3. **Consulta fundamentada**: preguntar por reglas o aclaraciones y poder inspeccionar fuentes, vigencia, conflictos e incertidumbre. El Assistant puede proponer cambios, pero no modifica Collection ni Decks.
4. **Metajuego**: realizar consultas con contexto temporal, regional o de formato. Es un caso funcional secundario y no un tercer bucle central de adopción.
5. La experiencia se cubre en español e inglés mediante una matriz repartida entre testers, incluyendo preguntas cuya fuente esté en el otro idioma.

El reporte contextual de errores dentro del producto no forma parte del MVP; durante la beta se usará comunicación externa con los devs.

### Recorrido del admin

Un Admin puede incorporar o actualizar una Knowledge source, revisar el conocimiento resultante, publicarlo o retirarlo y comprobar el efecto en respuestas posteriores. El cambio debe ser trazable y no requerir desplegar código. Solo los Admins curan conocimiento compartido.

### Señales de éxito

- La cohorte son amigos invitados; la validación es deliberadamente informal y admite ayuda de los devs.
- Como referencia, no como puerta formal de lanzamiento: reunir unos 10 testers activos, lograr que alrededor del 70% complete los dos bucles centrales y que alrededor del 50% vuelva a realizar una acción sustantiva en otra semana.
- Registrar si la finalización fue asistida permite interpretar fricción, pero no invalida el recorrido.
- El metajuego se acepta mediante casos funcionales de calidad, sin condicionar la señal de retorno.
- No puede cerrarse la beta con una regla inventada presentada como cierta, una cita falsa o una exposición de datos entre usuarios conocida y sin corregir.

Los métodos precisos, casos de regresión y umbrales técnicos pertenecen a **Definir la evaluación del asistente** y **Fijar los requisitos no funcionales del MVP**.
