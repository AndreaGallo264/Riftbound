# 02: Desplegar la shell bilingüe responsive

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Entregar la primera aplicación web desplegada y bilingüe, con navegación adaptable y conexiones gestionadas preparadas, para que el equipo pueda verificar un recorrido completo desde un cambio hasta un entorno accesible.

**Blocked by:** None (can start immediately).

**Status:** ready-for-agent

- [ ] Existe una aplicación Next.js TypeScript desplegable en Vercel y conectada a un proyecto Supabase europeo mediante configuración de entorno.
- [ ] La shell ofrece destinos Collection, Decks y Ask, además del acceso secundario a Imports y Admin cuando corresponda.
- [ ] Los controles pueden alternar entre español e inglés sin traducir nombres oficiales de Cards.
- [ ] Escritorio usa navegación persistente y móvil usa navegación inferior utilizable desde 320 px.
- [ ] CI ejecuta al menos formato/lint, comprobación de tipos, tests y build sobre cada cambio.
- [ ] Ningún secreto de Vercel, Supabase, Trigger.dev u otro proveedor llega al navegador o al repositorio.
- [ ] Un smoke test automatizado demuestra que la aplicación desplegada carga y permite cambiar de idioma.
