# 04: Aplicar ciclo de cuenta y aislamiento

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Aplicar los estados de cuenta y el aislamiento de datos como una frontera común, para que una identidad suspendida o ajena no pueda acceder a recursos privados aunque manipule peticiones.

**Blocked by:** 03: Entrar mediante invitación y magic link.

**Status:** ready-for-agent

- [ ] Las cuentas representan de forma inequívoca los estados `invited`, `active`, `suspended` y `deleted`.
- [ ] Suspender una cuenta revoca sus sesiones y bloquea nuevos accesos sin borrar todavía sus datos.
- [ ] Reactivar una cuenta suspendida permite volver a entrar mediante un nuevo magic link.
- [ ] Row Level Security niega por defecto el acceso entre testers y las rutas servidor conservan el mismo alcance.
- [ ] Alterar IDs de usuario o recursos en cliente no cambia el sujeto autenticado de una operación.
- [ ] Las credenciales privilegiadas solo se usan en servidor mediante rutas Admin explícitas.
- [ ] Pruebas negativas intentan leer y modificar datos centinela de otro tester y demuestran el rechazo.
