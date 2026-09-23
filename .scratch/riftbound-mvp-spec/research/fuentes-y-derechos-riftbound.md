# Fuentes y derechos para datos de Riftbound

**Fecha de consulta:** 2026-09-09
**Alcance:** catálogo de cartas, reglas, aclaraciones/rulings, listas competitivas y metajuego. Investigación acotada a páginas oficiales de Riot/Riftbound, documentos oficiales y páginas propias de servicios comunitarios.
**Nota:** esto es una evaluación técnica y de procedencia, no asesoramiento jurídico.

## Resumen ejecutivo

1. **La fuente de ingestión preferente para el catálogo es la API oficial de Riot.** El Developer Portal documenta `GET /riftbound/content/v1/contents` (`riftbound-content-v1`), con JSON de sets/cartas, arte, `version` y `lastUpdated`. La documentación de Riftbound exige una API key específica y aprobación del producto; una llamada sin credenciales devolvió HTTP 401 durante esta consulta.
2. **La fuente canónica de reglas es el Rules Hub oficial, no una copia comunitaria.** Enlaza los PDF vigentes de Core Rules y Tournament Rules, mantiene la legalidad/baneos y enlaza patch notes y erratas. Los FAQ oficiales se autodefinen como rulings oficiales y explican su precedencia frente al Core Rules Document.
3. **Riot publica listas y datos de metajuego en artículos oficiales de Organized Play**, incluidos campo, conversión implícita entre días y decklists completas. No hay una API oficial documentada para resultados, listas o metajuego.
4. **Existe una restricción crítica para el MVP:** la política específica de Riftbound prohíbe a las apps publicar o retener “metagame-defining data”, incluyendo play rates, win rates y diferencias de porcentaje por matchup. También prohíbe el uso “middle-man” que redistribuye datos de la API. Por tanto, no debe diseñarse un almacén propio de metajuego ni una API derivada sin aprobación escrita de Riot.
5. **Las plataformas comunitarias son útiles para descubrimiento y contraste, no como feeds autorizados por defecto.** Riftcodex sí ofrece REST/OpenAPI público sin autenticación, pero no publica términos/licencia de datos verificables. Piltover Archive prohíbe el scraping automatizado en sus términos. RiftDecks bloquea expresamente agentes y scraping competitivo en `robots.txt`. Riftbound.gg y Rift Atlas reservan derechos sobre su contenido/compilación y no documentan APIs públicas.
6. **Hay una transición operativa inmediata:** Riot anunció que el 2026-09-14 PlayRiftbound.com sustituirá a carde.io para registro, pairings y resultados; reconoce que las integraciones comunitarias que dependen de carde.io probablemente se interrumpirán. Cualquier integración competitiva debe aplazarse hasta observar la nueva plataforma y sus interfaces autorizadas.

## Matriz de fuentes

| Fuente | Cobertura y formato confirmado | Acceso, derechos y riesgo | Idioma y actualización observable | Valor para el MVP |
|---|---|---|---|---|
| **Riot Developer Portal: `riftbound-content-v1`** | API oficial JSON. Un endpoint: `GET /riftbound/content/v1/contents`. DTO con `game`, `version`, `lastUpdated`, sets y cartas; carta con ID, collector number, set, nombre, descripción, tipo, rareza, facción, stats, keywords, arte, flavor text y tags. | Requiere producto registrado, API key específica y aprobación discrecional. Riot puede limitar llamadas, revocar claves y exigir borrado al terminar. Solo pueden usarse assets Riftbound suministrados por la Riot API. No se permite redistribución tipo “middle-man”. La licencia es limitada, revocable y no transfiere propiedad. | Parámetro `locale`; la referencia indica “During beta only en available”. `version` y timestamp ISO permiten polling/detección de cambio, pero no se publica cadencia ni webhook. | **Fuente primaria recomendada** para Card catalog y assets tras aprobación. No cubre decklists/meta en el esquema observado. |
| **Card Gallery oficial** | Galería web oficial de sets/cartas. HTML Next.js con datos embebidos observables y assets en CDN de Riot/Sanity; no está documentada como API. | Acceso web público, pero los Terms de Riot reservan Game Content y restringen copia, distribución, reverse engineering y uso comercial salvo autorización. Que el JSON esté en HTML no otorga licencia de reutilización. | El sitio anuncia variantes `en-us`, `es-es`, `de-de`, `fr-fr`, `it-it`, `ja-jp`, `ko-kr`, `zh-cn`, `zh-tw`; la existencia de ruta no garantiza paridad de todas las cartas. Actualización al publicar Riot, sin SLA/feed documentado. | Fallback visual/manual y control de calidad. **No usar como ingesta automatizada de producción** si puede usarse la API aprobada. |
| **Rules Hub y PDF oficiales** | Página índice con legalidad construida/2v2, ban list, PDF de Core Rules y Tournament Rules, patch notes y erratas. En la consulta, ambos PDF ingleses constan como actualizados 2026-07-16. | Lectura pública. No se encontró una licencia abierta de redistribución de PDF/texto; enlazar y almacenar metadatos/procedencia es más prudente que republicar el documento íntegro. Los términos generales de Riot siguen aplicando. | Hub confirmado en inglés y francés; `es-es/rules-hub/` devolvió 404. El sitio general anuncia nueve locales, pero la cobertura por documento es desigual. Mecanismo: reemplazo de PDF + artículos fechados; sin feed/API específica confirmada. | **Canónico** para reglas, formato/legalidad y vigencia. Guardar URL, fecha declarada, hash y fecha de consulta; no asumir que una URL histórica sigue vigente. |
| **FAQ, patch notes y erratas oficiales** | Artículos HTML y, en algunos casos, PDF descargable. El FAQ Vendetta declara que es una colección de rulings oficiales: prevalece sobre el Core Rules Document cuando difieren, hasta que un nuevo Core Rules Document lo sustituya. Las erratas muestran texto nuevo/antiguo por carta. | Lectura pública; no hay licencia abierta específica. Deben citarse como Knowledge source, no copiarse masivamente sin autorización. | Principalmente inglés; hay publicaciones/localizaciones parciales, por ejemplo hub y errata francesa. Se publican por set y cuando Riot detecta aclaraciones; no hay periodicidad garantizada. | **Canónico** para Ruling y Card revision. Modelar precedencia, fecha de publicación y documento sucesor/obsoleto. |
| **Noticias oficiales de Organized Play** | Artículos HTML con evento, fecha, field share y decklists. “Barcelona’s Top Decks” publica 2.130 participantes del día 1, 379 del día 2, porcentajes por Legend y listas con main, battlefields, runes y sideboard. | Fuente oficial consultable, pero no se encontró licencia/API para reutilización masiva. Además, la política de apps de Riot prohíbe publicar o retener datos que definan el meta. | Artículos fechados, en el sitio localizado; publicación ligada a eventos, sin SLA. | Usar como **evidencia citada y acotada**, no como dataset acumulativo automático salvo aprobación expresa. |
| **Riftbound Gaming Network / carde.io (UVS)** | Sitio enlazado oficialmente por Riot. HTML público para eventos/tiendas y una sección de decks; login para funciones de cuenta. En la consulta, la página de eventos exponía filtros de fecha, lugar, formato y categoría. | No se localizó API pública ni términos específicos desde las rutas probadas. No asumir permiso para endpoints internos. | Interfaz observada en inglés. Los eventos son actualizados por organizadores/plataforma; sin cadencia publicada. Será sustituido como sistema de Organized Play el 2026-09-14. | Solo enlace/consulta manual durante la transición. **No construir integración nueva.** |
| **Riftcodex** | API comunitaria REST JSON funcional, OpenAPI 3.1 en `/openapi.json`, sin auth para lectura. Cards, sets e índices; paginación, búsqueda y filtros; IDs Riftbound/TCGplayer/Cardmarket; `metadata.updated_on`. | Se declara fan project bajo la fan content policy, pero no se encontraron Terms, Privacy ni licencia de datos en sus páginas propias (404). “Open API” describe acceso técnico, no una licencia jurídica. Procedencia upstream no está explicada de forma suficiente en docs/FAQ. | Documentación en inglés. Changelog; última entrada visible v0.2.1, 2026-07-10, con Vendetta y aviso de datos parciales hasta que se actualicen sus fuentes. Sin SLA/webhook. | Buen prototipo/contraste. **No dependencia de producción ni redistribución** hasta confirmar procedencia, licencia y compatibilidad con la política Riot. |
| **Piltover Archive** | Catálogo, deckbuilder, decks comunitarios y torneos. La página mostraba 1.238 cartas, 90.307 decks y torneos marcados BETA/incompletos. HTML server-rendered consultable; no API pública documentada. | Operador identificado (STGMNN Labs UG). Términos: uso personal/no comercial; contenido/compilación del operador o licenciantes; cada usuario conserva sus decklists y concede licencia al operador; prohíbe robots/spiders para sobrecargar o scrapear. La licencia concedida por usuarios al operador no se transmite a terceros. | Interfaz/contenido principal en inglés. Fechas relativas y anuncios; roadmap público, pero sin SLA de datos. Procedencia de cada deck puede ser usuario o cuenta “System”; no equivale automáticamente a resultado oficial. | Descubrimiento y enlaces a listas; pedir licencia/feed al operador antes de ingerir. No mezclar decks comunitarios con listas competitivas verificadas. |
| **Riftbound.gg (DotGG)** | Catálogo, decks, rules, tournaments, prices y artículos de meta. Los reportes publican field shares, resultados, win rates y muestras de partidas, pero el artículo revisado no identifica el feed/dataset upstream de esos números. No API pública documentada. | Términos: contenido original, features y funcionalidad pertenecen a DotGG/licenciantes; servicio “as is”. Se declara no afiliado con Riot/UVS y monetizado con afiliación/Premium. No se observó licencia de reutilización. Su oferta de estadísticas debe revisarse contra la prohibición de metagame-defining data; este informe **no afirma** si Riot la aprobó o no. | Inglés. Homepage y artículos muestran publicaciones/actualizaciones frecuentes, incluso diarias alrededor de eventos; sin SLA. | Fuente editorial secundaria para contraste. No ingerir estadísticas/listas sin permiso y procedencia por evento. |
| **Rift Atlas** | Galería, decks, búsqueda, sealed y simulador; selector confirmado EN/简体中文. No API pública documentada. | Operador identificado (S. Goerlitz UG). Fan project; Riot conserva cartas/assets. Términos reservan branding, texto, código y compilaciones propias, y advierten que datos pueden ser incompletos/desactualizados. No conceden licencia de extracción. Tiene membresías/entitlements; la conformidad con aprobación Riot no está verificada aquí. | Changelog propio con cambios diarios y páginas semanales; evidencia alta de actividad del servicio, no garantía de frescura del catálogo. | Referencia manual/UX y contraste bilingüe. No fuente de ingestión sin acuerdo. |
| **RiftDecks** | El buscador externo lo describe como base de top decks, pero el sitio devolvió 403 a las páginas probadas. Solo se pudo consultar su `robots.txt`. No API confirmada. | `robots.txt` bloquea ChatGPT/GPTBot/Claude y advierte explícitamente que no permite scraping por sitios similares que construyan un servicio competidor. No se pudieron verificar términos/licencia. | **No verificado**: idioma, procedencia y mecanismo de actualización. La frescura mostrada por un buscador no se considera evidencia primaria. | Excluir de ingestión. Contacto/licencia directa obligatorios incluso para evaluar un feed. |
| **Repositorios GitHub derivados** | `slimtreble/Riftbound-card-data`: JSON, CSV y scripts que extraen `__NEXT_DATA__` de la galería; distingue texto impreso de errata. `apitcg/riftbound-tcg-data`: JSON por cartas/sets con README mínimo. `KevPereira/RiftCardex-data`: manifest/sets/cards JSON derivados de Riftcodex. | En Slim Treble, MIT cubre **solo scripts**; README/licencia excluyen datos y arte Riot. `apitcg` y RiftCardex-data no mostraron licencia. Que GitHub permita descargar no concede derechos sobre datos/assets de Riot. | Slim Treble tuvo un único commit el 2026-07-28. `apitcg` no recibe commits desde 2026-02-26. RiftCardex-data reactivó catálogo v43 el 2026-09-08 tras estar parado desde junio; precios sí muestran commits diarios. | Útiles para estudiar esquemas y fallos, no como fuente canónica. La historia confirma riesgo de desactualización y cadena de procedencia larga. |

## Fuentes oficiales en detalle

### 1. Catálogo y API oficial

**Confirmado**

- El índice de APIs de Riot lista `riftbound-content-v1` como producto Riftbound.
- La referencia dinámica del endpoint documenta `GET /riftbound/content/v1/contents`, regiones AMERICAS/ASIA/EUROPE, respuesta JSON tipada, errores HTTP y `locale` opcional.
- La respuesta incluye `version` y `lastUpdated`, mecanismo suficiente para detectar actualizaciones sin comparar todo el catálogo.
- La guía de herramientas digitales afirma que la Riot API autoriza acceso a “select Riftbound assets”, incluyendo card art, rulesets y otros materiales. Sin embargo, **el único DTO visible en la referencia consultada contiene sets/cartas y no campos de reglas**. La disponibilidad de rulesets en el endpoint actual queda **no verificada**.
- El endpoint sin API key respondió 401 en los tres hosts regionales probados. La referencia genérica mostraba una opción “Not required”, inconsistente con la prueba y con la política; debe asumirse que requiere credencial.

**Condiciones relevantes confirmadas**

- El producto debe registrarse incluso si sirve a jugadores sin usar APIs documentadas.
- API key de producción: una por producto, secreta, uso HTTPS y aprobación discrecional/revocable.
- Casos normalmente aprobados: deckbuilders y card libraries.
- Solo assets Riftbound suministrados por Riot API; texto oficial inglés o traducción oficial disponible por API. Una traducción propia solo puede mostrarse junto al inglés oficial.
- Un deckbuilder debe implementar las reglas oficiales aplicables suministradas por la API.
- Prohibidos: redistribución “middle-man”; metagame-defining data; rankings/ladders alternativos; gambling; gameplay con reglas automatizadas; ciertos usos comerciales sin aprobación.
- Las API Terms permiten límites variables y exigen dejar de usar y borrar Game Information al terminar la licencia.

**Incertidumbres**

- No se publicó SLA, webhook, política de cache TTL ni rate limit específico de producción para Riftbound. Las API Terms solo fijan 10 llamadas/10 segundos para Development Key y permiten otros límites discrecionales.
- Las API Terms muestran “Last updated: 2013” y definiciones históricas de League of Legends, mientras las políticas Riftbound son de 2026. Deben interpretarse conjuntamente y cualquier conflicto debe elevarse a Developer Support.
- No se verificó que una cuenta o key de desarrollo tenga acceso inmediato a `riftbound-content-v1`; la guía habla de aprobación caso por caso.

### 2. Reglas, legalidad, erratas y rulings

El Rules Hub debe actuar como índice canónico. En vez de congelar una URL de PDF como verdad permanente, el importador debería consultar el hub, registrar:

- URL del hub y del documento enlazado;
- fecha de actualización declarada;
- fecha de consulta;
- hash del archivo;
- idioma;
- tipo (`Core Rules`, `Tournament Rules`, FAQ, patch notes, errata, ban list);
- relaciones de precedencia y obsolescencia.

La precedencia observada es relevante para el modelo:

- Tournament Rules prevalece sobre Core Rules en competición.
- La versión inglesa de Tournament Rules prevalece sobre traducciones oficiales.
- Un addendum oficial de evento puede prevalecer sobre Tournament Rules.
- El FAQ Vendetta prevalece sobre el Core Rules Document si difieren, hasta la publicación de un Core Rules Document nuevo.
- Un artículo histórico puede advertir expresamente que ya no representa las reglas actuales y remitir al Rules Hub.

Esto impide tratar un Ruling o una Card revision como una propiedad atemporal. Deben conservar fuente, autoridad, publicación y periodo de vigencia.

### 3. Competición y metajuego oficial

Los artículos de Organized Play demuestran que Riot publica tanto decklists como agregados. Esto los hace la fuente de mayor autoridad disponible para una observación de Metagame, pero no un feed técnico estable.

La transición anunciada para el 2026-09-14 cambia la procedencia operativa:

- carde.io/UVS era el sistema actual para localizar, registrar, ejecutar eventos y conservar historial;
- PlayRiftbound.com será propiedad de Riot y gestionará login con Riot ID, registro, pairings y resultados;
- Riot migrará el historial;
- Riot avisa que proyectos que dependen de datos carde.io “will likely be interrupted”; no promete API compatible;
- creación/validación de decklists y mejoras de visualización de cartas figuran como trabajo explorado, no como capacidades/API comprometidas.

**Conclusión:** hasta que Riot publique una interfaz o conceda acceso, las observaciones competitivas deberían entrar por revisión editorial de páginas oficiales, con volumen acotado y sin calcular/publicar métricas prohibidas.

## Fuentes comunitarias y procedencia

### Qué está confirmado

- **Riftcodex** es la única API comunitaria pública y documentada encontrada: REST JSON, OpenAPI 3.1, lectura sin auth, cards/sets/indexes, versionado y changelog.
- **Piltover Archive**, **Riftbound.gg** y **Rift Atlas** ofrecen páginas propias con catálogos y/o listas. Sus páginas legales identifican operador y reservan derechos; ninguna documenta un API público reutilizable.
- **RiftDecks** expresa técnicamente una negativa al scraping en `robots.txt` y bloquea estos agentes.
- Los repositorios derivados muestran que es técnicamente posible extraer el JSON embebido de la galería, pero también documentan que contiene texto impreso y puede no incorporar errata vigente.

### Qué no está verificado

- Que una plataforma comunitaria tenga aprobación/API key de Riot. Un aviso “created under Legal Jibber Jabber”, Riot Sign-On o uso de assets oficiales **no prueba por sí solo** aprobación del caso de uso completo.
- Que sus card texts estén sincronizados con erratas y traducciones vigentes.
- Que una lista etiquetada con un evento provenga del organizador, del jugador o de transcripción comunitaria, salvo que la página lo documente.
- Que sus estadísticas competitivas deriven de resultados completos, una muestra, partidas públicas o estimaciones editoriales.
- Que endpoints JSON internos observables puedan usarse por terceros. No se consideran API pública sin documentación y condiciones de acceso.
- Que “open”, “public” o una licencia MIT de software cubran nombres, textos, imágenes o compilaciones de cartas de Riot.

## Recomendación de arquitectura de fuentes

### Admitir en el MVP

1. **Card catalog:** Riot API aprobada; snapshot interno con `version`, `lastUpdated`, locale, timestamp y hash. No exponer un espejo/API de los datos.
2. **Card revision:** Riot API si entrega texto vigente; si no, base impresa oficial + erratas oficiales revisadas por Admin. Nunca promover automáticamente una extracción comunitaria a texto vigente.
3. **Reglas y rulings:** Rules Hub, PDF oficiales y artículos FAQ/patch/errata. Almacenar fragmentos mínimos necesarios, cita y precedencia; conservar enlace al original.
4. **Deck list competitiva:** artículos oficiales por evento, con atribución exacta, evento, fecha, jugador, puesto y método de captura. Revisión Admin antes de publicar.
5. **Metagame:** en el MVP, solo citas/resúmenes de publicaciones oficiales ya agregadas. No derivar ni retener play rates, win rates o matchup deltas sin aprobación explícita del Developer Portal.

### No admitir sin acuerdo adicional

- scraping de RiftDecks o Piltover Archive;
- consumo de endpoints internos de webs comunitarias;
- reexportar Riot API o Riftcodex como API propia;
- ingestión masiva de decks de usuario como si fueran listas competitivas;
- entrenamiento/embeddings masivos de PDFs, artículos o card art sin validar que la aprobación y licencia cubren ese tratamiento;
- almacenamiento de imágenes fuera de las condiciones de Riot API;
- cálculos propios de metajuego que entren en la definición prohibida de Riot.

### Diligencias antes de implementar

1. Registrar el MVP en Riot Developer Portal con mockup/flujo funcional y solicitar una API key específica.
2. Describir explícitamente en la solicitud: catálogo, colección privada, deckbuilder, preguntas sobre reglas y uso previsto de listas/metajuego.
3. Pedir respuesta escrita sobre cache/snapshots, embeddings o RAG, conservación tras revocación, uso de snippets de reglas y si una observación oficial de meta puede almacenarse sin recomputar métricas.
4. Consultar Developer Support sobre la aparente tensión entre la guía (“rulesets” por API) y el esquema actual, y sobre la inconsistencia de autenticación de la referencia.
5. Reevaluar PlayRiftbound.com después del 2026-09-14; no inferir contratos a partir de tráfico de navegador.
6. Si se desea una fuente comunitaria, negociar feed/licencia y exigir campos de procedencia por registro, política de corrección, idioma, timestamp y mecanismo de retirada.

## URLs consultadas

Todas las URLs de esta sección fueron consultadas el **2026-09-09**.

### Riot/Riftbound

- Sitio oficial: <https://playriftbound.com/en-us/>
- Card Gallery: <https://playriftbound.com/en-us/card-gallery/>
- Rules Hub (EN): <https://playriftbound.com/en-us/rules-hub/>
- Rules Hub (FR): <https://playriftbound.com/fr-fr/rules-hub/>
- Core Rules PDF enlazado por el hub: <https://cmsassets.rgpub.io/sanity/files/dsfx7636/news_live/e9ac8e3d33e0f78cef296f5945aba7bc1313b086.pdf>
- Tournament Rules PDF enlazado por el hub: <https://cmsassets.rgpub.io/sanity/files/dsfx7636/news_live/503da65669ced10598d62925a6f6bc15111af726.pdf>
- Vendetta FAQ/rulings: <https://playriftbound.com/en-us/news/rules-and-releases/vendetta-rules-faq-and-clarifications>
- Origins errata: <https://playriftbound.com/en-us/news/rules-and-releases/riftbound-origins-card-errata>
- Core Rules Unleashed patch notes: <https://playriftbound.com/en-us/news/rules-and-releases/riftbound-core-rules-unleashed-patch-notes>
- Tournament Rules histórico con aviso de obsolescencia: <https://playriftbound.com/en-us/news/announcements/tournament-rules-january-update>
- Barcelona top decks/meta oficial: <https://playriftbound.com/en-us/news/organizedplay/barcelonas-top-decks>
- Transición a nuevo Organized Play: <https://playriftbound.com/en-us/news/announcements/introducing-the-new-playriftboundcom>
- Riftbound Gaming Network/UVS: <https://locator.riftbound.uvsgames.com/>
- Índice de Riot APIs: <https://developer.riotgames.com/apis>
- Referencia `riftbound-content-v1`: <https://developer.riotgames.com/api-details/riftbound-content-v1>
- Guía Digital Tools de Riftbound: <https://developer.riotgames.com/docs/riftbound>
- Política API específica de Riftbound: <https://developer.riotgames.com/policies/riftbound>
- Políticas generales: <https://developer.riotgames.com/policies/general>
- API Terms: <https://developer.riotgames.com/terms>
- Riot Terms of Service: <https://www.riotgames.com/en/terms-of-service>
- Legal Jibber Jabber/fan policy: <https://www.riotgames.com/en/legal>
- Sitemap de locales: <https://playriftbound.com/sitemap_index.xml>

### Comunidad

- Riftcodex: <https://riftcodex.com/>
- Riftcodex docs: <https://riftcodex.com/docs>
- Riftcodex Cards API: <https://riftcodex.com/docs/endpoints/cards>
- Riftcodex OpenAPI: <https://api.riftcodex.com/openapi.json>
- Riftcodex changelog: <https://riftcodex.com/changelog>
- Riftcodex FAQ: <https://riftcodex.com/faq>
- Piltover Archive: <https://piltoverarchive.com/>
- Piltover cards: <https://piltoverarchive.com/cards>
- Piltover decks: <https://piltoverarchive.com/decks>
- Piltover tournaments: <https://piltoverarchive.com/tournaments>
- Piltover Terms: <https://piltoverarchive.com/terms-of-service>
- Piltover Imprint: <https://piltoverarchive.com/imprint>
- Riftbound.gg: <https://riftbound.gg/>
- Riftbound.gg About: <https://riftbound.gg/about/>
- Riftbound.gg Terms: <https://riftbound.gg/terms/>
- Ejemplo de reporte de meta: <https://riftbound.gg/singapore-regional-qualifier/>
- Rift Atlas: <https://riftatlas.com/>
- Rift Atlas changelog: <https://riftatlas.com/changelog>
- Rift Atlas Terms: <https://riftatlas.com/terms-of-service>
- Rift Atlas Legal Notice: <https://riftatlas.com/legal-notice>
- RiftDecks robots: <https://riftdecks.com/robots.txt>
- Dataset derivado Slim Treble: <https://github.com/slimtreble/Riftbound-card-data>
- Dataset derivado apitcg: <https://github.com/apitcg/riftbound-tcg-data>
- Dataset derivado RiftCardex: <https://github.com/KevPereira/RiftCardex-data>
