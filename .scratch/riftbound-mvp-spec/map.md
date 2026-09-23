# Encontrar la especificación del MVP del asistente de colección Riftbound

Label: `wayfinder:map`

## Destination

Una especificación implementable de un MVP web bilingüe (español/inglés) para beta cerrada que permita registrar colecciones y mazos de Riftbound y formular consultas citadas sobre reglas, aclaraciones, la colección propia, los mazos y el metajuego.

## Notes

- Dominio: catálogo de cartas, colección por jugador, mazos, reglas y rulings con procedencia, y metajuego acotado temporalmente.
- Consultar las skills `grilling` y `domain-modeling` para decisiones HITL, `research` para hechos externos y `prototype` para validar comportamiento o experiencia.
- Las reglas proceden solo de documentos oficiales vigentes; su evidencia debe estar disponible bajo demanda y, ante conflicto o falta de respuesta oficial, el producto no debe fingir certeza.
- El metajuego se limita a observaciones y listas oficiales dentro de su entorno competitivo; no se calculan ni retienen estadísticas agregadas prohibidas por la política de Riot.
- Beta cerrada multiusuario e informal con amigos; solo admins incorporan o corrigen conocimiento y las métricas orientan, no bloquean formalmente el lanzamiento.
- Interfaz y respuestas bilingües español/inglés; las fuentes pueden estar en cualquiera de ambos idiomas.
- Favorecer coste mínimo, servicios gestionados y poca carga operativa para un equipo de dos devs.
- Wayfinder planifica decisiones; no implementa el producto.

## Decisions so far

- [Definir los recorridos y el éxito del MVP](issues/01-definir-recorridos-y-exito-del-mvp.md): dos bucles centrales de colección y mazo con consultas trazables, operación editorial sin deploy y validación informal mediante uso, retorno y ausencia de fallos críticos abiertos.
- [Investigar las fuentes y los derechos de los datos de Riftbound](issues/02-investigar-fuentes-y-derechos-de-datos.md): prioriza API y Rules Hub oficiales; fuentes comunitarias y datos de metajuego requieren cautela de procedencia, licencia y autorización.
- [Definir el modelo de catálogo, colección y mazo](issues/03-definir-modelo-de-catalogo-coleccion-y-mazo.md): separa identidad jugable, revisiones, impresiones y copias físicas; los mazos usan cartas y cantidades sin reservar ejemplares de la colección.
- [Fijar la autoridad, vigencia y resolución de conflictos entre fuentes](issues/04-fijar-autoridad-vigencia-y-conflictos.md): las reglas actuales se basan solo en documentos oficiales, con inglés autoritativo, precedencia explícita, fuentes bajo demanda y abstención ante vacíos o conflictos.
- [Definir el ciclo de vida del conocimiento](issues/05-definir-ciclo-de-vida-del-conocimiento.md): carga manual y publicación atómica por un Admin, con revisiones inmutables, reindexación incremental, retirada y rollback auditables sin reentrenar el LLM.
- [Definir el contrato de respuesta del asistente](issues/06-definir-contrato-de-respuesta-del-asistente.md): respuestas breves ampliables en el idioma de la pregunta, contexto privado actual, estados explícitos, evidencia bajo demanda y recomendaciones separadas sin fallback a memoria del LLM.
- [Delimitar el metajuego y las recomendaciones de mazos](issues/07-delimitar-metajuego-y-recomendaciones.md): evidencia solo oficial y vigente para el mismo entorno, sin estadísticas derivadas; recomendaciones legales separan opciones con la colección de una lista ideal.
- [Definir el comportamiento de colecciones y mazos](issues/08-definir-comportamiento-de-colecciones-y-mazos.md): edición e importación con previsualización, borradores persistentes, exportación y separación estricta entre legalidad del mazo y cobertura de la colección.
- [Definir el acceso y la administración de la beta cerrada](issues/09-definir-acceso-y-administracion-de-la-beta.md): acceso por invitación y enlace mágico, aislamiento entre testers, inspección administrativa, suspensión reversible, conversaciones privadas y borrado autoservicio.
- [Prototipar la experiencia bilingüe de colección y consultas](issues/10-prototipar-la-experiencia-bilingue.md): combina Collection visual de C con Deck y Assistant de A, panel contextual adaptable, Ask independiente y navegación inferior móvil.
- [Elegir la arquitectura gestionada de datos e IA](issues/11-elegir-arquitectura-gestionada-de-datos-e-ia.md): monolito Next.js sobre Vercel/Supabase EU, jobs Trigger.dev, SQL más búsqueda híbrida Postgres y OpenAI reemplazable con datos mínimos y validación servidor.
- [Definir la evaluación del asistente](issues/12-definir-evaluacion-del-asistente.md): suite bilingüe de 40 casos con checks deterministas y LLM juez, cero fallos críticos, umbrales 100/95/90 y regresiones versionadas para cambios sensibles.
- [Fijar los requisitos no funcionales del MVP](issues/13-fijar-requisitos-no-funcionales-del-mvp.md): beta best effort de hasta 25 usuarios, tope de 25 USD, RPO/RTO de 24 h, seguridad y observabilidad mínimas, accesibilidad básica y compatibilidad móvil/escritorio.

## Not yet specified

## Out of scope

- Compra, venta, precios, valoración monetaria y marketplace.
- Funciones sociales, perfiles públicos, torneos y emparejamientos.
- Reconocimiento o importación de cartas mediante imágenes o cámara.
- Preentrenamiento o fine-tuning de un LLM propio.
