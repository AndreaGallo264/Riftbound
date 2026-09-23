# 03: Entrar mediante invitación y magic link

**Parent:** [MVP del asistente de colección Riftbound](../../riftbound-mvp-spec/SPEC.md)

**What to build:** Permitir que una persona invitada acepte su invitación e inicie sesión mediante un enlace mágico temporal, manteniendo cerrada la beta y protegidas las rutas privadas.

**Blocked by:** 02: Desplegar la shell bilingüe responsive.

**Status:** ready-for-agent

- [ ] No existe registro público y una dirección no invitada no puede crear una cuenta activa.
- [ ] Un Admin puede generar, reenviar y revocar una invitación vinculada a un email mediante una operación protegida inicial.
- [ ] Aceptar una invitación válida crea o activa la cuenta correcta y permite solicitar un magic link.
- [ ] Magic links expirados, revocados o reutilizados producen un error comprensible y no crean una sesión.
- [ ] Las rutas privadas redirigen a acceso y las rutas de autenticación devuelven al destino solicitado tras iniciar sesión.
- [ ] La interfaz informa que los Admins pueden inspeccionar datos privados para soporte antes de aceptar la beta.
- [ ] Tests de navegador cubren invitación, login, logout y rechazo de acceso no invitado.
