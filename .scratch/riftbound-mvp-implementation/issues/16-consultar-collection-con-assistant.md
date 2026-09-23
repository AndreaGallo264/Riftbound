# 16: Consultar la Collection con el Assistant

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Permitir preguntas sobre la Collection privada mediante tools tipadas y de solo lectura que consulten siempre el último estado guardado y expliquen cantidades sin exponer datos ajenos.

**Blocked by:** 06: Gestionar Owned copies manualmente; 15: Aplicar recuperación híbrida y contrato de respuesta.

**Status:** ready-for-agent

- [ ] El compositor puede seleccionar `My collection` y muestra claramente ese contexto.
- [ ] Las tools consultan SQL parametrizado dentro del alcance autenticado y devuelven resultados estructurados mínimos.
- [ ] Cada petición lee el último estado guardado, aunque la Conversation contenga cifras antiguas.
- [ ] El Assistant puede contar, agrupar y explicar Owned copies sin convertir datos privados en Knowledge source.
- [ ] La evidencia privada identifica entidad y versión o instante de lectura sin publicar contenido a otros testers.
- [ ] El Assistant no crea, edita ni elimina Owned copies y cualquier propuesta se muestra fuera de controles de confirmación.
- [ ] Tests cubren frescura, cantidades, ausencia de Collection, aislamiento y resistencia a IDs ajenos en el prompt.
