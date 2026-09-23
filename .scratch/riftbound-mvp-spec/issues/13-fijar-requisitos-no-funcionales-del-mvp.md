# Fijar los requisitos no funcionales del MVP

Type: `grilling`
Status: `resolved`
Blocked by: 01, 09, 11, 12

## Question

¿Qué objetivos medibles de coste, latencia, disponibilidad, privacidad, seguridad, observabilidad, capacidad y retención necesita la beta para que la especificación sea implementable por dos devs?

## Answer

### Coste y disponibilidad

- El gasto total objetivo es `0–25 USD/mes`, sin contar dominio, usando free tiers y pago por uso durante la beta.
- Se generan alertas al alcanzar el `70%` y `90%` del presupuesto mensual.
- Al alcanzar el `100%`, se bloquean nuevas llamadas al LLM y el Assistant responde `unavailable`; Collection, Decks, exportación y administración siguen disponibles.
- La beta opera en modalidad best effort, sin SLA ni porcentaje de uptime prometido. Mantenimientos e incidentes conocidos se comunican a los amigos por el canal externo acordado.
- Las dependencias degradadas deben producir estados visibles; nunca aparentar éxito ni usar memoria del LLM como fallback.

### Rendimiento

- No se fijan umbrales de latencia antes de observar tráfico real.
- Se miden p50/p95 para carga de páginas, operaciones de Collection/Deck, tiempo al primer token, respuesta completa y duración de jobs de ingestión.
- Cada release sensible conserva una línea base comparable; regresiones claras se investigan, pero no existe una puerta numérica durante esta beta.

### Capacidad y límites

- Hasta 25 cuentas invitadas, aproximadamente 10 activas y 5 sesiones concurrentes sin rediseño.
- Hasta 10.000 Owned copies y 100 Decks por Beta tester.
- Máximo 20 consultas al Assistant por tester y hora, con dos ejecuciones simultáneas por tester.
- CSV: máximo 10 MB y 10.000 filas.
- PDF oficial: máximo 25 MB y 300 páginas.
- Los límites se validan antes de subir/procesar y producen errores comprensibles, sin trabajo parcial silencioso.

### Recuperación y retención

- Objetivos `RPO <= 24 h` y `RTO <= 24 h`.
- Backup lógico cifrado diario en almacenamiento separado del Postgres primario, con siete días de retención.
- Se prueba una restauración antes de abrir la beta y después de cambios relevantes del esquema o mecanismo de backup.
- Collection, Decks y Conversations se conservan hasta borrado por el usuario o eliminación de cuenta.
- El borrado elimina inmediatamente los datos activos; sus copias expiran con la rotación de backups en un máximo de siete días.
- Logs operativos y trazas se conservan 14 días.
- Knowledge revisions y auditoría editorial se conservan mientras lo permitan los derechos aplicables; una obligación de eliminación prevalece y deja solo el tombstone técnico permitido.

### Privacidad y seguridad

- TLS en tránsito y cifrado gestionado por proveedor en reposo.
- RLS obligatoria para datos por tester, con pruebas negativas que intentan acceder mediante IDs de otro usuario.
- Service keys y secretos solo en entornos servidor/Trigger.dev; nunca llegan al navegador, repositorio o logs.
- Magic links temporales, revocación de sesiones al suspender/borrar y protección contra reutilización.
- Buckets privados; tipo, tamaño y contenido básico de uploads se validan antes de procesar.
- Dependencias y secretos se escanean en CI; vulnerabilidades críticas conocidas bloquean despliegue.
- El borrado de cuenta y aislamiento forman parte de pruebas automatizadas.
- Conforme a la decisión previa, las lecturas Admin de datos privados no tienen auditoría individual. Publicaciones y cambios editoriales sí mantienen auditoría completa.

### Observabilidad

- Registrar errores, estados/reintentos de jobs, disponibilidad de proveedores, latencias, tokens, coste y consumo de cuotas.
- Logs y métricas usan IDs técnicos, no contenido completo de prompts, respuestas, Conversations, Collection o Decks.
- Los errores correlacionan request, tester de forma seudonimizada, run de LLM, job y Knowledge publication sin exponer secretos.
- Alertas mínimas: presupuesto 70/90/100%, fallos repetidos de ingestión, incremento de errores de autenticación/RLS y proveedor LLM no disponible.

### Accesibilidad y compatibilidad

- Se aplican buenas prácticas básicas sin declarar conformidad formal WCAG: HTML semántico, uso completo por teclado, foco visible, contraste legible, labels asociados, errores anunciables y estados que no dependan solo del color.
- Smoke test con VoiceOver y escaneo axe sin violaciones críticas en los recorridos centrales antes de abrir la beta.
- Diseño utilizable desde 320 px sin ocultar Collection, Decks, Ask ni acciones críticas.
- Soporte para las dos versiones más recientes de Chrome, Firefox y Safari, más Safari iOS y Chrome Android actuales.

Estos requisitos son límites del MVP, no compromisos de producción. Superar capacidad, presupuesto o disponibilidad esperada obliga a reevaluar planes y arquitectura antes de ampliar la beta.
