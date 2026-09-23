# Definir el comportamiento de colecciones y mazos

Type: `grilling`
Status: `resolved`
Blocked by: 01, 03

## Question

¿Cómo crean, editan e importan los beta testers sus colecciones y mazos, qué validaciones reciben y qué operaciones debe poder ejecutar o explicar el asistente sobre esos datos?

## Answer

### Collection

- El Beta tester busca una Card o Printing y puede añadir una o varias Owned copies, indicando idioma, acabado, condición y nota opcional.
- La edición manual permite modificar o eliminar cada Owned copy y realizar ajustes de cantidad como operaciones por lote sobre copias equivalentes.
- Eliminar una Owned copy no modifica ningún Deck; recalcula su Collection coverage y puede producir nuevos faltantes.

### Importación de Collection

- El MVP admite una plantilla CSV propia, además de edición manual. No intenta interpretar formatos de plataformas externas.
- Una fila identifica Card/Printing y puede indicar cantidad para crear varias Owned copies con los mismos atributos.
- Toda importación genera una previsualización con altas, actualizaciones, eliminaciones, advertencias y errores antes de escribir datos.
- Una coincidencia ambigua o inexistente queda pendiente para que el usuario elija una Card/Printing o descarte la fila; nunca se decide silenciosamente.
- El usuario elige modo `append` o `replace`. `append` añade nuevas copias; `replace` sustituye la Collection solo después de confirmar la previsualización completa.
- El CSV exportado conserva identificadores de Owned copy para que su reimportación pueda actualizar copias existentes sin duplicarlas.
- Un error no aplica parcialmente la importación: después de resolver o descartar filas problemáticas, la confirmación se ejecuta como un único cambio.

### Decks

- El Beta tester puede crear, renombrar, duplicar y eliminar un Deck; elegir Deck format; y añadir, quitar o mover entradas `Card + cantidad` entre Deck sections.
- Puede importar un Deck pegando una lista de texto simple o mediante CSV propio. La previsualización resuelve nombres ambiguos, secciones y formato antes de confirmar.
- Un Deck ilegal, incompleto o con Cards no poseídas puede guardarse como borrador y seguir editándose.
- Cambiar Deck format conserva sus entradas y vuelve a calcular la validación; no elimina Cards automáticamente.
- Deck legality muestra por separado errores de reglas/formato y casos que no pudieron validarse por falta de datos oficiales.
- Collection coverage muestra cantidades poseídas y faltantes para ese Deck. No afecta a su legalidad y no reserva copias frente a otros Decks.

### Exportación

- La Collection se exporta en el mismo CSV documentado que admite la importación.
- Cada Deck se exporta como lista de texto y como CSV propio, conservando formato, secciones y cantidades.

### Assistant

- Consulta siempre el último estado guardado de Collection y del Deck activo o nombrado.
- Puede calcular y explicar cantidades, Collection coverage, Deck legality y efectos de cambios propuestos.
- Puede devolver propuestas estructuradas de cambios, incluida la versión limitada a la Collection y la versión ideal con faltantes.
- No crea, edita, importa, elimina ni confirma datos. El usuario realiza cualquier cambio mediante controles explícitos fuera del chat.

La forma visual de búsquedas, previsualizaciones, errores y propuestas pertenece a **Prototipar la experiencia bilingüe de colección y consultas**.
