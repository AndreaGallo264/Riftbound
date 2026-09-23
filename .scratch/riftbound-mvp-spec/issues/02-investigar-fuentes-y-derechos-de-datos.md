# Investigar las fuentes y los derechos de los datos de Riftbound

Type: `research`
Status: `resolved`

## Question

¿Qué fuentes oficiales y comunitarias existen para cartas, reglas, aclaraciones, listas competitivas y metajuego de Riftbound, y qué formatos, condiciones de acceso, licencias, procedencia, cobertura lingüística y ritmos de actualización ofrece cada una?

## Answer

Informe completo: [Fuentes y derechos para datos de Riftbound](../research/fuentes-y-derechos-riftbound.md).

La investigación y una verificación directa de la URL aportada por el equipo confirman estas conclusiones:

- El [Rules Hub oficial](https://playriftbound.com/en-us/rules-hub/) es el índice canónico de reglas vigentes. Reúne legalidad y baneos, Core Rules, Tournament Rules, patch notes y erratas, con fechas declaradas de actualización.
- El catálogo debería proceder de la API oficial `riftbound-content-v1`, que exige registrar el producto, obtener aprobación y usar una API key. Incluye versión y fecha de actualización, pero no ofrece SLA ni webhook publicados.
- FAQ, patch notes y erratas oficiales deben modelarse como fuentes fechadas con relaciones de precedencia y obsolescencia; una regla o Card revision no puede tratarse como atemporal.
- No se encontró una API oficial documentada para resultados, decklists o metajuego. Riot prohíbe a las aplicaciones publicar o retener datos que definan el metajuego, incluidos play rates y win rates, sin autorización aplicable.
- Riftcodex ofrece una API comunitaria pública y útil para prototipos, pero su licencia de datos y procedencia no están suficientemente documentadas. Las demás plataformas comunitarias revisadas no ofrecen feeds reutilizables por defecto y algunas prohíben scraping.
- El Rules Hub y otros recursos oficiales tienen cobertura lingüística desigual. El producto debe conservar idioma, URL, fecha declarada, fecha de consulta y hash de cada fuente, sin asumir paridad español/inglés.
- La lectura pública no equivale a licencia abierta. Para el MVP es más prudente almacenar procedencia y fragmentos mínimos necesarios, enlazar el original y pedir confirmación escrita a Riot sobre snapshots, RAG/embeddings, reglas y metajuego.

El informe local sustituye el puntero de rama porque este directorio no es un repositorio Git.
