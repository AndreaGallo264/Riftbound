# Prototipar la experiencia bilingüe de colección y consultas

Type: `prototype`
Status: `resolved`
Blocked by: 01, 06, 08, 09

## Question

¿Qué estructura de navegación e interacción permite que un beta tester gestione cartas y mazos, formule preguntas con contexto y evalúe fuentes, vigencia e incertidumbre sin que la interfaz confunda datos propios con conocimiento global?

## Answer

Prototipo primario: [Tres variantes de experiencia bilingüe](../prototypes/bilingual-experience-prototype.html). Es un HTML autónomo y descartable con variantes `?variant=A`, `?variant=B` y `?variant=C`; el repositorio no usa git, por lo que el asset local sustituye a la rama throwaway.

### Dirección validada

La experiencia final combina estructuras, no los tres estilos visuales completos:

- **Collection** adopta el archivador visual de la variante C: conteo, búsqueda y alta visibles; Cards/Printings reconocibles como objetos de colección; densidad adaptable sin convertir todo en tabla.
- **Deck** adopta la mesa de mando de la variante A: composición densa, Deck legality y Collection coverage simultáneas, acciones de edición/exportación y Assistant al lado.
- **Assistant** adopta el panel de la variante A. Desde Collection o Deck conserva contexto explícito y actualizado; puede plegarse en escritorio y ocupa una pantalla completa en móvil.
- **Ask** existe como destino independiente para preguntas sin una entidad abierta. Usa el mismo Assistant a ancho completo y permite seleccionar Current rules, Collection o un Deck como contexto.
- La variante B no se adopta como estructura principal, aunque valida que una pregunta global puede empezar seleccionando contexto antes de enviarse.

### Navegación

- Escritorio: navegación persistente a Collection, Decks, Ask e Imports; el contenido central cambia por ruta y el Assistant contextual ocupa el panel derecho cuando corresponde.
- Móvil: barra inferior persistente con Collection, Decks y Ask. Imports y acciones secundarias viven dentro de su ruta relacionada.
- Abrir/cerrar el panel nunca pierde el contexto seleccionado ni convierte datos privados en conocimiento global.

### Señales visibles de contexto y confianza

- El compositor muestra un chip con `Current rules`, `My collection` o el nombre y versión actual del Deck utilizado.
- Cada respuesta muestra su estado (`grounded`, falta de contexto, ausencia de respuesta oficial, conflicto o indisponibilidad) antes del texto.
- Facts y Recommendations aparecen separados.
- Las fuentes permanecen plegadas bajo demanda y muestran sus metadatos al abrirse.
- La interfaz responde en el idioma de la pregunta; los controles pueden cambiar entre español e inglés sin traducir nombres oficiales de Cards.

### Validación del prototipo

- Las tres variantes y parámetros de URL respondieron correctamente mediante servidor local.
- El JavaScript embebido pasó comprobación de sintaxis con Node.
- El diseño incluye adaptación para escritorio, tablet y móvil, navegación por teclado entre variantes y respeto por `prefers-reduced-motion`.

La implementación debe crear un sistema visual coherente para la combinación elegida; no debe copiar simultáneamente las paletas y tipografías incompatibles de A y C. El prototipo es evidencia de estructura e interacción, no código de producción.
