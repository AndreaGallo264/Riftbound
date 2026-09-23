# Elegir la arquitectura gestionada de datos e IA

Type: `grilling`
Status: `resolved`
Blocked by: 03, 05, 06, 07, 08, 09

## Question

¿Qué arquitectura de aplicación, datos, búsqueda/recuperación y proveedor de LLM satisface las decisiones funcionales y editoriales con el menor coste y carga operativa razonables, manteniendo reemplazables el modelo y las fuentes?

## Answer

Investigación comparativa: [Opciones de arquitectura gestionada para el MVP](../research/managed-architecture-options.md).

### Plataforma

- **Aplicación:** monolito modular TypeScript con Next.js, desplegado en Vercel y organizado por los módulos de identidad, catálogo, Collection, Decks, conocimiento, Assistant y administración.
- **Datos:** Supabase en región europea para Postgres, Auth, Storage privado, Row Level Security y `pgvector`.
- **Procesamiento asíncrono:** Trigger.dev para extracción de PDF, chunking, embeddings, reintentos e indexación. El estado durable de cada etapa permanece en Postgres.
- **IA inicial:** OpenAI detrás de Vercel AI SDK y de interfaces propias para generación y embeddings. El modelo generativo concreto se fija mediante evaluación y configuración, no en código de dominio.
- **Presupuesto:** Vercel Hobby y Supabase Free durante la beta informal, Trigger.dev Free/Hobby y OpenAI pay-as-you-go con límites de gasto.

Los free tiers no ofrecen SLA y pueden pausar o limitar recursos. Se acepta un único deployer en Vercel durante la beta. Si se requiere colaboración gestionada o continuidad estable, el salto esperado de Vercel + Supabase ronda `45–65 USD/mes` antes de IA y jobs.

### Autoridad de datos

- Postgres es el sistema de registro para usuarios, Card catalog, Collections, Decks, Conversations, Knowledge revisions/publications, jobs y auditoría editorial.
- Collection coverage, Deck legality, permisos y transiciones editoriales se calculan de forma determinista en aplicación/SQL; nunca se delegan al LLM.
- RLS aísla todos los datos por Beta tester. Las credenciales de servicio solo existen en código servidor y jobs; el acceso Admin usa rutas privilegiadas explícitas.
- Los archivos se suben directamente a buckets privados de Supabase para evitar límites de payload de Vercel.
- Importaciones `append`/`replace` y activación de Knowledge publications se confirman mediante transacciones atómicas.

### Ingestión

El pipeline ejecutado por Trigger.dev sigue etapas idempotentes:

1. registrar upload/URL y Knowledge revision en `draft`;
2. validar propietario, tipo, tamaño, hash y procedencia;
3. extraer texto y estructura de forma determinista;
4. generar fragmentos con posición/página y metadatos;
5. crear embeddings por lotes;
6. ejecutar validaciones y dejar el draft listo para revisión;
7. tras aprobación Admin, activar publicación e índice en una transacción corta.

Cada etapa registra versión del pipeline, input hash, intento y error. Un fallo conserva la última publicación válida. El callback del LLM o del job nunca publica conocimiento directamente.

### Recuperación

- **Datos privados y catálogo:** consultas SQL/tools de solo lectura con parámetros y resultados tipados.
- **Conocimiento:** búsqueda híbrida dentro de Postgres, combinando full-text search por idioma y similitud de `pgvector` mediante Reciprocal Rank Fusion.
- Todo candidato se filtra antes de responder por Knowledge publication activa, autoridad, vigencia, idioma y tipo de fuente.
- Se empieza con búsqueda vectorial exacta para el corpus pequeño. HNSW solo se añade si mediciones posteriores justifican latencia y demuestran recall suficiente bajo filtros.
- Cada embedding conserva proveedor, modelo, dimensiones, versión de chunking/pipeline y hash. Cambiar embeddings crea un índice paralelo y reindexa; nunca mezcla espacios vectoriales.

### Assistant

- El servidor selecciona tools y evidencia; OpenAI recibe únicamente fragmentos y campos privados mínimos necesarios para la pregunta.
- Vercel AI SDK normaliza streaming, tool calling y salida estructurada, pero una interfaz propia evita que Conversation o dominio dependan de IDs y estado del proveedor.
- La salida usa un schema validado con estado de respuesta, hechos, Recommendations y `source_ids` existentes. El servidor construye enlaces/citas desde esos IDs y rechaza referencias inexistentes o inactivas.
- Conversations se conservan en Postgres; no se usa almacenamiento conversacional propietario de OpenAI como sistema de registro.
- No hay segundo proveedor operativo en el MVP. Si OpenAI falla, el contrato devuelve `unavailable`.
- OpenAI es reemplazable, pero cambiar de modelo exige ejecutar la evaluación bilingüe; cambiar de embedding exige reindexación versionada.

### Portabilidad y límites

- Mantener SQL/Postgres, `pgvector`, object storage tras una interfaz, schemas propios y jobs que referencian IDs de dominio limita el lock-in.
- No introducir vector DB separado, microservicios, colas adicionales ni fallback multi-LLM hasta que exista una necesidad medida.
- Configurar alertas y caps para OpenAI/Trigger.dev y monitorizar cuotas de Vercel/Supabase.
- Registrar el producto en Riot Developer Portal antes de usar la API oficial en producción.
- La ingestión de texto, fragmentos o embeddings de material oficial queda bloqueada hasta confirmar que la autorización de Riot cubre API, almacenamiento y RAG. Mientras tanto solo se conservan metadatos/enlaces y datos de prueba autorizados.

Los objetivos cuantitativos de seguridad, disponibilidad, backups, latencia y costes se fijan en **Fijar los requisitos no funcionales del MVP**; el modelo generativo se acepta en **Definir la evaluación del asistente**.
