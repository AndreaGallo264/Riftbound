# 24: Evaluar y seleccionar el Assistant

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Crear una evaluación reproducible que bloquee regresiones críticas y seleccione el modelo generativo más barato que cumpla el contrato bilingüe completo.

**Blocked by:** 15: Aplicar recuperación híbrida y contrato de respuesta; 17: Consultar y mejorar un Deck con el Assistant; 22: Responder sobre Metagame sin agregados prohibidos; 23: Conectar fuentes autorizadas de producción.

**Status:** ready-for-agent

- [ ] La suite contiene los 40 casos sintéticos versionados y la distribución de categorías definida en la especificación.
- [ ] Cada caso conserva input, contexto mínimo, publicación aplicable, estado/respuesta esperada, fuentes y rúbrica.
- [ ] Checks deterministas validan schema, estado, source IDs, aislamiento, tool y cálculos sin delegarlos al juez.
- [ ] Un LLM juez fijado evalúa semántica, apoyo de citas, abstención, equivalencia bilingüe y separación Facts/Recommendations.
- [ ] Casos críticos se ejecutan tres veces y cualquier exposición, regla inventada, cita inválida, publicación retirada, fallback a memoria, schema o cálculo incorrecto bloquea.
- [ ] Se aplican umbrales de 100% determinista, 95% estado/recuperación top cinco y 90% semántico.
- [ ] Cada run conserva versiones, configuración, coste y latencia y selecciona el candidato más barato que aprueba.
