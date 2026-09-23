# Definir el modelo de catálogo, colección y mazo

Type: `grilling`
Status: `resolved`

## Question

¿Qué identidades, variantes, cantidades, estados y relaciones debe distinguir el MVP entre cartas del catálogo, copias poseídas, colecciones y mazos para responder correctamente a consultas del usuario?

## Answer

El MVP separa la identidad jugable de una carta, sus publicaciones físicas y los ejemplares concretos del jugador.

### Catálogo

- **Card** es una identidad jugable estable.
- **Card revision** contiene sus datos y texto oficial efectivos durante un periodo. Una revisión nueva sustituye a la anterior sin cambiar la identidad de Card.
- **Printing** representa una publicación física de una Card, distinguida por lanzamiento/edición, número de coleccionista o arte.
- El catálogo conserva revisiones con su vigencia; no sobrescribe silenciosamente datos oficiales anteriores.

### Colección

- Cada Beta tester mantiene una sola **Collection**.
- La Collection contiene **Owned copies** individuales, no cantidades agregadas.
- Cada Owned copy pertenece a una Printing y registra idioma, acabado o foil, condición física y una nota opcional.
- El precio, historial de adquisición, ubicación y préstamos quedan fuera de este modelo del MVP.
- Las cantidades disponibles se calculan contando Owned copies de la Card correspondiente.

### Mazos

- Cada **Deck** pertenece a un Beta tester y declara un **Deck format**.
- El Deck agrupa entradas `Card + cantidad` en **Deck sections** definidas por el formato.
- Un Deck puede contener Cards que no estén en la Collection.
- Los Decks no reservan ni enlazan Owned copies concretas. Varios Decks pueden usar la misma Card y cada uno calcula sus faltantes independientemente contra la Collection.
- Cualquier Owned copy de la Card cuenta para disponibilidad sin exigir una Printing, idioma, acabado o condición determinados.

La legalidad del Deck, sus faltantes y las cantidades son resultados derivados del catálogo, las reglas del Deck format, sus entradas y la Collection; no son identidades independientes. La forma de editar, importar y reconciliar estos datos se decide en **Definir el comportamiento de colecciones y mazos**.
