# 28: Validar la apertura de la beta

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Ejecutar una puerta final reproducible sobre los recorridos completos, seguridad, accesibilidad, compatibilidad y recuperación antes de invitar a los amigos a usar la beta.

**Blocked by:** 08: Importar Collection con previsualización atómica; 11: Importar y exportar Decks; 20: Operar cuentas y soporte desde Admin; 24: Evaluar y seleccionar el Assistant; 25: Aplicar cuotas y degradación por presupuesto; 26: Observar aplicación, jobs y proveedores; 27: Respaldar, restaurar y expirar datos.

**Status:** ready-for-agent

- [ ] Recorridos E2E cubren invitación, Collection manual/CSV, Deck manual/importado, Ask, fuentes, Conversations, Admin y borrado de cuenta.
- [ ] Pruebas de integración confirman RLS, estados, importaciones atómicas, cálculos, publicación/rollback y borrado.
- [ ] La suite del Assistant aprueba todos los umbrales y no tiene barreras críticas abiertas.
- [ ] Escaneo de dependencias y secretos no presenta vulnerabilidades críticas conocidas ni credenciales expuestas.
- [ ] VoiceOver y axe no encuentran violaciones críticas en los recorridos centrales; teclado, foco, labels, errores y contraste son utilizables.
- [ ] Los recorridos funcionan desde 320 px en las versiones soportadas de Chrome, Firefox, Safari, Safari iOS y Chrome Android.
- [ ] Backup/restauración, alertas y degradación por presupuesto se han ensayado y sus resultados quedan registrados.
- [ ] La beta se comunica como best effort sin SLA y los testers conocen soporte externo, privacidad Admin y límites aplicables.
