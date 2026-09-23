# Definir el acceso y la administración de la beta cerrada

Type: `grilling`
Status: `resolved`
Blocked by: 01, 05

## Question

¿Qué límites de cuenta, invitación, aislamiento de datos y permisos distinguen a beta testers y admins, y qué herramientas mínimas necesitan los admins para operar la beta y curar conocimiento?

## Answer

### Acceso y estados de cuenta

- No existe registro público. Un Admin invita una dirección de email y el Beta tester accede mediante un enlace mágico temporal, sin contraseña propia.
- Una invitación está vinculada a su email, puede reenviarse o revocarse y solo crea una cuenta al aceptarse.
- Las cuentas pasan por `invited`, `active`, `suspended` y `deleted`.
- Suspender revoca sesiones y bloquea nuevos accesos, pero conserva Collection, Decks y Conversations para una posible reactivación.
- El rol Admin se asigna mediante configuración técnica. El panel no permite promover Beta testers; inicialmente los dos devs son Admins.

### Aislamiento y acceso administrativo

- Cada Beta tester solo puede leer o modificar su propia Collection, sus Decks y sus Conversations.
- Cualquier operación del Assistant se ejecuta dentro del alcance del tester autenticado; una referencia aportada por el usuario no permite cambiar ese alcance.
- Los Admins pueden inspeccionar siempre cuentas, Collections, Decks y Conversations para soporte. El MVP no registra cada lectura administrativa.
- Esta capacidad administrativa debe comunicarse claramente a los testers al aceptar la invitación; los datos siguen siendo privados frente a otros testers.
- El acceso editorial de un Admin no convierte datos privados en Knowledge source ni permite incorporarlos al conocimiento compartido.

### Conversaciones y borrado

- Las Conversations se guardan por tester para mantener continuidad y pueden borrarse individualmente o en conjunto.
- El Beta tester dispone de borrado autoservicio de cuenta con confirmación explícita e irreversible.
- El borrado elimina acceso, Collection, Decks y Conversations. Solo pueden persistir registros técnicos mínimos cuando sean necesarios por seguridad u obligación aplicable; nunca quedan disponibles al Assistant.
- Antes de borrar, el tester puede usar las exportaciones de Collection y Decks ya definidas.

### Herramientas mínimas de Admin

- Invitar, reenviar o revocar invitaciones.
- Consultar estado básico de cuenta y suspender o reactivar acceso.
- Inspeccionar datos privados para soporte.
- Cargar Knowledge sources, revisar drafts y diferencias, publicar, retirar y ejecutar rollback según el ciclo editorial resuelto.
- Ver fallos de extracción/indexación y el historial auditable de cambios editoriales.

Quedan fuera del MVP la edición de perfiles ajenos, la suplantación de usuario, la promoción de roles desde la interfaz y la analítica administrativa avanzada. Los mecanismos concretos de autenticación, autorización y eliminación física se decidirán en **Elegir la arquitectura gestionada de datos e IA** y **Fijar los requisitos no funcionales del MVP**.
