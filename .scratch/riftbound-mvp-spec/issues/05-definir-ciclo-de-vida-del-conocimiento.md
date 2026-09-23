# Definir el ciclo de vida del conocimiento

Type: `grilling`
Status: `resolved`
Blocked by: 02, 04

## Question

¿Cómo incorporan los admins una fuente nueva o una corrección, cómo se revisa, versiona, sustituye o retira su conocimiento, y qué trazabilidad debe conservar el MVP para que actualizar el corpus no implique reentrenar el LLM?

## Answer

### Incorporación

- El MVP no descubre ni publica fuentes automáticamente. Un Admin inicia cada cambio cargando manualmente una URL o archivo.
- La carga crea una **Knowledge revision** inmutable en estado `draft`; nunca modifica la versión activa.
- El sistema extrae fragmentos y metadatos, calcula diferencias respecto de la revisión anterior y prepara una vista previa.
- El Admin revisa como mínimo identidad y tipo de fuente, URL, idioma, fechas declaradas y de consulta, hash, fragmentos, relaciones de precedencia/sustitución y errores de extracción.

### Corrección y aprobación

- Un solo Admin puede aprobar, adecuado para una beta informal operada por dos devs.
- En conocimiento de reglas, el Admin solo corrige fidelidad técnica: extracción, segmentación, metadatos o traducción para que reflejen la Official rules source.
- El Admin no puede añadir una interpretación propia, completar áreas grises ni convertir contenido comunitario en una regla.
- Cada aprobación registra actor, instante, revisión aprobada y motivo o nota del cambio.

### Publicación

- Aprobar crea una **Knowledge publication** y activa conjuntamente la revisión y sus artefactos de recuperación; los usuarios nunca ven una actualización parcial.
- Solo se reindexizan o recalculan embeddings de fragmentos añadidos, modificados o retirados. El LLM no se reentrena ni conserva conocimiento nuevo por sí mismo.
- Las respuestas solo consultan revisiones publicadas y activas; drafts y publicaciones fallidas quedan excluidos.
- Si extracción, validación o indexación falla, la última publicación válida permanece activa.

### Sustitución, retirada y rollback

- Publicar una revisión posterior marca la anterior como `superseded`; retirar una fuente marca su publicación activa como `withdrawn`.
- Ningún cambio sobrescribe ni borra el historial normal. Revisiones, publicaciones, actores, fechas, hashes, relaciones y resultados del proceso permanecen auditables.
- Un rollback no reactiva silenciosamente una publicación antigua: crea una nueva Knowledge publication basada en la revisión elegida y registra el motivo.
- Si derechos o políticas externas exigen borrar contenido, se elimina lo exigido y se conserva únicamente un registro de auditoría sin el material restringido.

Este flujo permite que el conocimiento cambie sin despliegue de código y sin entrenar el modelo. Los detalles de almacenamiento, extracción, chunking, embeddings y activación pertenecen a **Elegir la arquitectura gestionada de datos e IA**.
