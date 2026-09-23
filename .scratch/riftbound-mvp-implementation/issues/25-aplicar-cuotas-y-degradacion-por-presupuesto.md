# 25: Aplicar cuotas y degradación por presupuesto

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Limitar cargas y consumo del Assistant y degradar únicamente la IA al alcanzar el presupuesto, manteniendo disponibles los datos y operaciones deterministas.

**Blocked by:** 13: Publicar y versionar conocimiento; 15: Aplicar recuperación híbrida y contrato de respuesta.

**Status:** ready-for-agent

- [ ] Se permiten como máximo 20 consultas al Assistant por tester y hora y dos ejecuciones simultáneas por tester.
- [ ] Collection limita 10.000 Owned copies y Decks limita 100 por tester con errores comprensibles antes de escribir.
- [ ] CSV y PDF aplican los límites de tamaño, filas y páginas antes de crear trabajo parcial.
- [ ] El coste mensual de proveedores se agrega contra un objetivo configurable de 25 USD.
- [ ] Se emiten alertas al 70% y 90% y se bloquean nuevas llamadas LLM al 100%.
- [ ] Al bloquear IA, Assistant devuelve `unavailable` mientras Collection, Decks, exportación y Admin continúan operativos.
- [ ] Tests cubren cuotas, concurrencia, límites y degradación sin fallback a memoria.
