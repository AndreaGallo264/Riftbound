# MVP del asistente de colección Riftbound

Status: `ready-for-agent`

## Problem Statement

Los jugadores de Riftbound necesitan mantener un inventario fiable de sus cartas, construir mazos y resolver dudas sobre reglas sin alternar entre hojas de cálculo, documentos oficiales y herramientas desconectadas. Las reglas, erratas, legalidad y publicaciones competitivas cambian con el tiempo, tienen cobertura lingüística desigual y no siempre resuelven las áreas grises. Una respuesta generada sin procedencia, con información obsoleta o mezclando datos de otros jugadores resulta peor que no responder.

El equipo, formado por dos desarrolladores, necesita validar con una beta cerrada e informal que una única aplicación bilingüe puede unir Collection, Decks y un Assistant fundamentado. El MVP debe ser barato de operar, actualizar el conocimiento sin reentrenar el LLM y respetar las restricciones de Riot sobre catálogo, contenido oficial y datos de Metagame.

## Solution

Construir una aplicación web bilingüe, accesible por invitación, donde cada Beta tester pueda mantener una Collection de Owned copies, crear o importar Decks y consultar un Assistant que use el Current rules state, el Card catalog y sus datos privados actuales.

La aplicación separará cálculos deterministas de generación: Deck legality, Collection coverage, permisos y transiciones editoriales se resolverán mediante lógica de aplicación y base de datos; el LLM explicará resultados y producirá Recommendations estructuradas usando únicamente evidencia recuperada. Las respuestas mostrarán estados explícitos, distinguirán hechos de Recommendations y permitirán inspeccionar sus fuentes bajo demanda.

Los Admins podrán cargar manualmente Official rules sources, revisar su extracción y publicar Knowledge revisions de forma atómica y auditable. La actualización del conocimiento reindexará solo los fragmentos afectados y nunca entrenará el modelo. El producto no ingerirá en producción datos o contenido de Riot sin una autorización o licencia que cubra almacenamiento, procesamiento y RAG.

## User Stories

1. Como Beta tester invitado, quiero aceptar una invitación vinculada a mi email, para acceder a la beta sin registro público.
2. Como Beta tester, quiero iniciar sesión mediante un enlace mágico temporal, para no gestionar otra contraseña.
3. Como Beta tester suspendido, quiero que mis sesiones sean revocadas, para impedir el acceso hasta que un Admin reactive mi cuenta.
4. Como Beta tester, quiero conocer que los Admins pueden inspeccionar mis datos para soporte, para entender el alcance real de su privacidad.
5. Como Beta tester, quiero alternar los controles entre español e inglés, para usar la aplicación en mi idioma preferido.
6. Como Beta tester, quiero conservar los nombres oficiales de las Cards aunque cambie el idioma de la interfaz, para evitar identificaciones ambiguas.
7. Como Beta tester, quiero buscar Cards y Printings del Card catalog, para identificar correctamente mis cartas físicas.
8. Como Beta tester, quiero añadir una o varias Owned copies, para representar cada ejemplar de mi Collection.
9. Como Beta tester, quiero registrar Printing, idioma, acabado, condición y una nota en una Owned copy, para distinguir mis ejemplares físicos.
10. Como Beta tester, quiero editar o eliminar una Owned copy concreta, para mantener mi Collection actualizada.
11. Como Beta tester, quiero ajustar por lote varias Owned copies equivalentes, para evitar operaciones manuales repetitivas.
12. Como Beta tester, quiero importar mi Collection mediante la plantilla CSV del producto, para cargar muchas cartas de una vez.
13. Como Beta tester, quiero previsualizar altas, actualizaciones, eliminaciones, advertencias y errores de una importación, para saber qué cambiará antes de confirmarla.
14. Como Beta tester, quiero resolver o descartar filas ambiguas de una importación, para que el sistema nunca elija una Card o Printing silenciosamente.
15. Como Beta tester, quiero elegir entre importación `append` y `replace`, para añadir copias o sustituir la Collection conscientemente.
16. Como Beta tester, quiero que una importación se confirme atómicamente, para no dejar mi Collection parcialmente modificada ante un error.
17. Como Beta tester, quiero reimportar un CSV exportado sin duplicar Owned copies, para poder editar mis datos externamente con seguridad.
18. Como Beta tester, quiero exportar mi Collection al mismo formato CSV admitido para importar, para conservar o trasladar mis datos.
19. Como Beta tester, quiero crear, renombrar, duplicar y eliminar Decks, para organizar distintas construcciones.
20. Como Beta tester, quiero elegir el Deck format y organizar Cards por Deck sections, para representar correctamente la estructura del mazo.
21. Como Beta tester, quiero importar un Deck desde texto simple o CSV, para evitar introducir cada Card manualmente.
22. Como Beta tester, quiero revisar nombres, secciones y formato ambiguos antes de confirmar una importación de Deck, para evitar interpretaciones silenciosas.
23. Como Beta tester, quiero guardar un Deck ilegal, incompleto o con Cards que no poseo como borrador, para poder desarrollarlo gradualmente.
24. Como Beta tester, quiero cambiar el Deck format sin perder sus Cards, para comparar la construcción bajo otro conjunto de reglas.
25. Como Beta tester, quiero ver Deck legality separada de Collection coverage, para no confundir incumplimientos de reglas con cartas faltantes.
26. Como Beta tester, quiero que eliminar una Owned copy recalcule los faltantes sin modificar mis Decks, para conservar mis construcciones.
27. Como Beta tester, quiero usar la misma Owned copy como cobertura de varios Decks sin reservarla, para evaluar cada mazo independientemente.
28. Como Beta tester, quiero exportar cada Deck como texto y CSV con formato, secciones y cantidades, para compartirlo o conservarlo.
29. Como Beta tester, quiero preguntar al Assistant por una regla, para obtener una respuesta breve y fundamentada en Official rules sources vigentes.
30. Como Beta tester, quiero preguntar por mi Collection completa, para conocer cantidades y opciones disponibles.
31. Como Beta tester, quiero consultar un Deck activo o nombrado, para recibir explicaciones y Recommendations contextualizadas.
32. Como Beta tester, quiero que cada pregunta use el último estado guardado de mi Collection y Deck, para no recibir respuestas basadas en datos obsoletos del chat.
33. Como Beta tester, quiero ver qué contexto usa el Assistant, para distinguir Current rules, My collection y un Deck concreto.
34. Como Beta tester, quiero que el Assistant pida aclaración cuando una Card, Deck, formato u objetivo ambiguo cambie la respuesta, para no recibir una suposición arbitraria.
35. Como Beta tester, quiero que el Assistant responda en el idioma de mi pregunta, para conversar naturalmente.
36. Como Beta tester, quiero que el Assistant avise cuando traduzca una fuente inglesa, para reconocer cuál es el texto autoritativo.
37. Como Beta tester, quiero distinguir Facts de Recommendations, para no confundir una preferencia con una regla.
38. Como Beta tester, quiero desplegar título, enlace, fecha, idioma y fragmento de las fuentes, para comprobar el fundamento de una respuesta.
39. Como Beta tester, quiero ver un estado explícito cuando falte contexto, no exista respuesta oficial, haya conflicto o falle un servicio, para no interpretar incertidumbre como certeza.
40. Como Beta tester, quiero que el Assistant se abstenga si no recupera evidencia suficiente, para que la memoria general del LLM no sustituya una fuente.
41. Como Beta tester, quiero que una respuesta de reglas aplique precedencia, vigencia y ámbito de las fuentes oficiales, para reflejar el Current rules state.
42. Como Beta tester, quiero recibir una Recommendation limitada a mi Collection y otra ideal con Cards faltantes, para comparar una mejora inmediata con una meta deseada.
43. Como Beta tester, quiero que las Recommendations expliquen reglas, sinergias y evidencia competitiva utilizada, para entender su razonamiento.
44. Como Beta tester, quiero que las afirmaciones de Metagame estén limitadas al Competitive environment de una publicación oficial, para no extrapolar evidencia obsoleta.
45. Como Beta tester, quiero que el producto no presente rankings o porcentajes propios de Metagame, para evitar métricas no autorizadas o engañosas.
46. Como Beta tester, quiero que el Assistant proponga cambios sin ejecutarlos, para conservar control explícito sobre Collection y Decks.
47. Como Beta tester, quiero navegar entre Collection, Decks y Ask desde móvil, para completar los recorridos centrales desde una pantalla pequeña.
48. Como Beta tester, quiero abrir un Assistant contextual junto a Collection o Deck en escritorio, para consultar sin perder de vista mis datos.
49. Como Beta tester, quiero usar Ask como destino independiente y seleccionar contexto, para hacer preguntas sin abrir previamente una entidad.
50. Como Beta tester, quiero borrar Conversations concretas o todas juntas, para controlar mi historial.
51. Como Beta tester, quiero exportar mis datos y borrar mi cuenta mediante confirmación explícita, para abandonar la beta y eliminar mis datos activos.
52. Como Admin, quiero invitar, reenviar y revocar invitaciones, para controlar quién accede a la beta.
53. Como Admin, quiero suspender y reactivar cuentas, para resolver problemas de acceso sin borrar datos inmediatamente.
54. Como Admin, quiero inspeccionar cuentas, Collections, Decks y Conversations para soporte, para ayudar a los testers cuando sea necesario.
55. Como Admin, quiero cargar manualmente una URL o archivo como Knowledge source, para incorporar una actualización oficial sin desplegar código.
56. Como Admin, quiero revisar metadatos, fragmentos, diferencias y relaciones de precedencia de una Knowledge revision, para detectar errores antes de publicarla.
57. Como Admin, quiero corregir extracción, segmentación, metadatos o traducción sin alterar el significado oficial, para mantener fidelidad a la fuente.
58. Como Admin, quiero publicar una Knowledge revision y su índice atómicamente, para que los testers nunca consulten una actualización parcial.
59. Como Admin, quiero que un fallo de extracción o indexación conserve la última Knowledge publication válida, para no degradar respuestas existentes.
60. Como Admin, quiero retirar, sustituir o ejecutar rollback mediante una nueva Knowledge publication auditable, para cambiar el corpus sin borrar su historial.
61. Como Admin, quiero ver fallos y reintentos de ingestión, para diagnosticar una actualización bloqueada.
62. Como desarrollador, quiero que el aislamiento por Beta tester se aplique en base de datos y servidor, para impedir acceso cruzado incluso si se manipulan identificadores.
63. Como desarrollador, quiero mantener cálculo determinista y generación separados, para que el LLM no decida legalidad, cantidades, permisos ni transiciones editoriales.
64. Como desarrollador, quiero poder sustituir el modelo generativo detrás de una interfaz estable, para comparar coste y calidad sin cambiar el dominio.
65. Como desarrollador, quiero versionar embeddings, chunking y pipeline, para reindexar sin mezclar espacios vectoriales incompatibles.
66. Como desarrollador, quiero ejecutar una suite bilingüe versionada antes de cambios sensibles, para detectar regresiones de grounding, privacidad y comportamiento.
67. Como desarrollador, quiero recibir alertas de presupuesto y bloquear llamadas al LLM al agotar el tope, para mantener el coste de la beta bajo control.
68. Como desarrollador, quiero observar errores, jobs, latencias, tokens, costes y cuotas sin registrar contenido privado completo, para operar la beta sin exponer datos innecesarios.

## Implementation Decisions

- La aplicación será un monolito modular TypeScript con Next.js. Los módulos principales serán identidad, catálogo, Collection, Decks, conocimiento, Assistant y administración.
- Vercel alojará la aplicación y Supabase, en región europea, proporcionará Postgres, Auth, Storage privado, Row Level Security y `pgvector`.
- Trigger.dev ejecutará extracción de PDF, chunking, embeddings, reintentos e indexación. Postgres conservará el estado durable e idempotente de cada etapa.
- El presupuesto de la beta se apoyará en Vercel Hobby, Supabase Free, Trigger.dev Free/Hobby y OpenAI pay-as-you-go, aceptando ausencia de SLA y un único deployer en Vercel.
- Postgres será el sistema de registro para cuentas, Card catalog, Collections, Decks, Conversations, Knowledge revisions, Knowledge publications, jobs y auditoría editorial.
- Una Card tendrá identidad jugable estable; Card revisions representarán texto y atributos oficiales durante periodos de vigencia; Printings representarán publicaciones físicas.
- Cada Beta tester tendrá una sola Collection compuesta por Owned copies individuales. Las cantidades se derivarán contando copias, no se almacenarán como inventario agregado independiente.
- Un Deck pertenecerá a un tester, declarará Deck format y contendrá entradas Card más cantidad agrupadas por Deck sections. No reservará Owned copies concretas.
- Deck legality y Collection coverage serán resultados derivados e independientes. Se calcularán de forma determinista mediante aplicación o SQL.
- Las importaciones de Collection tendrán modos `append` y `replace`, una previsualización resoluble y una confirmación transaccional. Los identificadores exportados permitirán reimportar sin duplicar.
- Las importaciones de Deck aceptarán texto simple y CSV propio. Un Deck no válido podrá guardarse como borrador y cambiar de formato sin eliminar automáticamente sus entradas.
- No habrá registro público. Supabase Auth gestionará invitaciones por email y enlaces mágicos. Las cuentas usarán los estados `invited`, `active`, `suspended` y `deleted`.
- Los roles serán Beta tester y Admin. El rol Admin se asignará mediante configuración técnica, no desde la interfaz.
- RLS aislará Collection, Decks y Conversations por tester. Las service keys existirán solo en servidor y jobs. El acceso privilegiado de Admin usará rutas explícitas.
- Los Admins podrán inspeccionar datos privados para soporte, pero esas lecturas no tendrán auditoría individual en el MVP. La actividad editorial sí será auditable.
- El borrado de cuenta eliminará inmediatamente los datos activos y revocará sesiones. Las copias de backup expirarán en un máximo de siete días.
- Las Official rules sources vigentes serán la única autoridad normativa. La versión inglesa prevalecerá y se aplicarán relaciones explícitas de ámbito, precedencia y sustitución.
- Foros y contenido comunitario no podrán fundamentar reglas. Las fuentes competitivas comunitarias permanecerán excluidas hasta contar con procedencia y autorización explícitas.
- El MVP responderá solo sobre el Current rules state. No reconstruirá reglas históricas.
- Una Knowledge revision será inmutable y empezará como `draft`. Una Knowledge publication activará de forma atómica una revisión y sus artefactos de recuperación.
- La publicación, sustitución, retirada y rollback conservarán actor, instante, motivo, hashes y relaciones. Un rollback creará una nueva publicación en lugar de reactivar silenciosamente una anterior.
- Los uploads irán directamente a buckets privados. Antes de procesarlos se validarán propiedad, tipo, tamaño, hash, procedencia y contenido básico.
- La ingestión será idempotente y separará registro, validación, extracción, chunking, embeddings, validaciones y activación. Un fallo conservará la publicación anterior.
- El Card catalog y los datos privados se consultarán mediante SQL/tools de solo lectura, parametrizados y tipados.
- El conocimiento se recuperará mediante búsqueda híbrida Postgres: full-text search por idioma más similitud `pgvector`, combinadas mediante Reciprocal Rank Fusion.
- La recuperación filtrará primero por publicación activa, autoridad, vigencia, idioma y tipo de fuente. Se empezará con búsqueda vectorial exacta; HNSW requerirá necesidad medida.
- OpenAI será el proveedor inicial para generación y embeddings, detrás de Vercel AI SDK e interfaces propias. El modelo concreto se elegirá mediante la suite de evaluación y configuración.
- No habrá fallback multi-LLM. Si OpenAI o la recuperación fallan, el Assistant devolverá `unavailable`.
- Cada embedding conservará proveedor, modelo, dimensiones, versión de chunking/pipeline y hash. Un cambio de embeddings generará un índice paralelo y una reindexación completa.
- El servidor seleccionará tools y evidencia y enviará al proveedor únicamente los fragmentos y datos privados mínimos para responder.
- La salida del Assistant será estructurada y validada. Incluirá estado, hechos, Recommendations y `source_ids` existentes; el servidor construirá las citas y rechazará referencias inexistentes o inactivas.
- Los estados de respuesta serán `grounded`, `needs_clarification`, `no_official_answer`, `official_conflict`, `missing_context` y `unavailable`.
- El Assistant nunca usará memoria general para suplir una fuente ausente, una recuperación fallida o datos privados no disponibles.
- Las Conversations se conservarán en Postgres; ningún almacenamiento conversacional del proveedor será el sistema de registro.
- El Metagame se limitará a observaciones y Competitive reference decks publicados oficialmente dentro de su Competitive environment. No se calcularán ni retendrán rankings, play rates, win rates ni agregados equivalentes.
- Para prototipar el Card catalog se podrá usar localmente `slimtreble/Riftbound-card-data` como fixture reemplazable. Su licencia MIT cubre solo los scripts; los datos, texto y arte pertenecen a Riot, no se consideran open source y no se desplegarán como fuente de producción.
- El producto no almacenará en producción datos de catálogo, texto, fragmentos o embeddings de Riot hasta contar con una autorización o licencia que cubra esos usos. Mientras tanto trabajará con metadatos, enlaces y datos de prueba autorizados.
- La interfaz combinará una Collection visual, un espacio denso para Deck con Assistant contextual y una ruta Ask independiente.
- En escritorio habrá navegación persistente y Assistant lateral plegable. En móvil habrá navegación inferior para Collection, Decks y Ask; el Assistant contextual ocupará pantalla completa.
- El compositor mostrará el contexto actual y cada respuesta mostrará su estado antes del texto. Facts, Recommendations y fuentes desplegables serán visualmente distintos.
- La aplicación será utilizable desde 320 px y soportará las dos versiones recientes de Chrome, Firefox y Safari, además de Safari iOS y Chrome Android actuales.
- La beta admitirá hasta 25 cuentas invitadas, unas 10 activas y cinco sesiones concurrentes; hasta 10.000 Owned copies y 100 Decks por tester.
- Se limitará a 20 consultas del Assistant por tester y hora y dos ejecuciones simultáneas por tester. CSV tendrá 10 MB y 10.000 filas; PDF oficial, 25 MB y 300 páginas.
- El objetivo de gasto será `0-25 USD/mes`, sin dominio. Habrá alertas al 70% y 90%; al 100% se bloquearán nuevas llamadas al LLM sin desactivar Collection, Decks, exportación o administración.
- La beta será best effort, sin SLA. Se medirán latencias y regresiones, pero no habrá una puerta numérica de rendimiento antes de observar tráfico real.
- Los objetivos serán `RPO <= 24 h` y `RTO <= 24 h`, con backup lógico cifrado diario separado, retención de siete días y restauración probada.
- Logs y trazas se conservarán 14 días usando identificadores técnicos y seudónimos, sin prompts, respuestas, Conversations, Collection o Decks completos.
- La interfaz aplicará HTML semántico, teclado completo, foco visible, contraste legible, labels, errores anunciables y estados que no dependan solo del color.

## Testing Decisions

- Los tests comprobarán comportamiento observable y contratos públicos; no dependerán de componentes internos, prompts exactos, consultas SQL concretas ni detalles del proveedor.
- La frontera principal serán recorridos end-to-end en navegador para invitación y login, Collection manual/CSV, Decks, Ask contextual, fuentes, Conversations, borrado de cuenta y operación editorial Admin.
- La segunda frontera serán pruebas de integración servidor/Postgres para invariantes deterministas: RLS, alcance de usuario, estados de cuenta, atomicidad de importaciones, Deck legality, Collection coverage, publicación atómica, retirada, rollback y borrado.
- La tercera frontera será una suite bilingüe versionada del Assistant con 40 casos sintéticos: 10 reglas directas, 6 precedencia/errata/legalidad, 6 abstención/conflicto/fallo de recuperación, 6 Collection, 6 Deck legality/coverage, 4 Recommendations/Metagame y 2 aislamiento.
- Los casos repartirán español, inglés, fuentes en idioma distinto y nombres oficiales de Cards entre todas las categorías.
- Checks deterministas validarán schema, estado, source IDs activos, aislamiento, tool elegido y cálculos de Collection/Deck.
- Un LLM juez fijado y más capaz evaluará corrección semántica, apoyo de citas, abstención, equivalencia bilingüe y separación entre Facts y Recommendations. No podrá invalidar una barrera determinista.
- Serán fallos críticos: exposición entre testers, regla sin apoyo oficial presentada como cierta, cita inventada o irrelevante, uso de publicación retirada, fallback factual a memoria del LLM, schema inválido y cálculo determinista incorrecto.
- Los casos críticos se ejecutarán tres veces y cualquier repetición fallida bloqueará. El resto se ejecutará una vez.
- Los objetivos serán cero fallos críticos; 100% de schema, aislamiento, source IDs y cálculos; al menos 95% de estado correcto y fuente esperada entre los cinco primeros resultados; y al menos 90% de aprobación semántica.
- La suite completa se ejecutará antes de abrir la beta y al cambiar modelo, embeddings, prompt de sistema, tools, schema, retrieval, chunking, ingestión o reglas que afecten casos existentes.
- Cada ejecución conservará versiones de suite, modelos, prompts, retrieval, pipeline y Knowledge publication, además de métricas, coste y latencia.
- Se elegirá el modelo generativo más barato que cumpla barreras y umbrales. Cambiar el juez abrirá una serie de resultados nueva y no mezclable.
- Habrá pruebas negativas que intenten acceder mediante IDs de otro tester, pruebas de revocación de magic links/sesiones y pruebas automatizadas de borrado de cuenta.
- Antes de abrir la beta se probará una restauración de backup, los recorridos centrales con VoiceOver y un escaneo axe sin violaciones críticas.
- No existe aplicación previa de la que reutilizar tests; estas tres fronteras constituyen la estrategia inicial acordada.

## Out of Scope

- Compra, venta, precios, valoración monetaria y marketplace.
- Funciones sociales, perfiles públicos, torneos y emparejamientos.
- Reconocimiento o importación de cartas mediante imágenes o cámara.
- Preentrenamiento o fine-tuning de un LLM propio.
- Registro público, contraseñas propias y promoción de Admins desde la interfaz.
- Perfiles complejos, suplantación de usuarios y analítica administrativa avanzada.
- Formatos de importación pertenecientes a plataformas externas.
- Reserva de Owned copies entre Decks.
- Reconstrucción histórica de reglas.
- Uso de foros o fuentes comunitarias como autoridad normativa.
- Agregación propia de estadísticas de Metagame.
- Segundo proveedor LLM operativo, vector database separada, microservicios o colas adicionales.
- SLA, garantía formal de disponibilidad o conformidad WCAG declarada.
- Reporte contextual de errores dentro de la aplicación durante la beta.

## Further Notes

- La beta se realizará informalmente con amigos. Las señales aproximadas de 10 testers activos, 70% completando Collection y Deck, y 50% regresando otra semana orientan al equipo, pero no son puertas formales.
- No se puede considerar aceptable una beta con una regla inventada, una cita falsa o una exposición conocida de datos entre usuarios sin corregir.
- El prototipo autónomo valida estructura e interacción, no código ni sistema visual de producción. La implementación combinará sus decisiones de Collection, Deck y Assistant bajo un lenguaje visual coherente.
- La investigación confirmó el Rules Hub como índice canónico. Aunque `riftbound-content-v1` existe, el MVP no dependerá de esa API por ahora.
- `slimtreble/Riftbound-card-data` puede acelerar el prototipo local, pero su propia licencia excluye los datos y activos de Riot; no resuelve el gate legal de producción.
- Antes de producción, el equipo debe obtener y conservar una base de uso verificable para snapshots, almacenamiento, extracción, RAG/embeddings, catálogo y evidencia competitiva.
- Los free tiers no garantizan continuidad. Si la beta requiere colaboración gestionada o estabilidad superior, el coste de Vercel y Supabase puede superar el objetivo mensual y obligará a revisar arquitectura o presupuesto.
- Esta especificación sintetiza las trece decisiones cerradas del mapa Wayfinder. Su siguiente transformación es una lista de tickets de implementación en slices verticales; no debe iniciarse esa división hasta que el repositorio compartido esté disponible.
