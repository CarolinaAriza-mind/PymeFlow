# 02 — Requisitos del producto

## 1. Requisitos funcionales

### RF-01 — Comercio y acceso

- El usuario puede registrar un comercio.
- El usuario puede iniciar y cerrar sesión.
- El sistema identifica el comercio activo y el rol del usuario.
- Los endpoints protegidos validan identidad, pertenencia y permisos en el backend.

### RF-02 — Usuarios

- El administrador puede consultar y gestionar miembros del comercio.
- Los roles iniciales son Administrador y Empleado.
- Un usuario no puede concederse permisos desde el frontend.

### RF-03 — Categorías

- Crear, listar, editar y desactivar categorías.
- No permitir duplicados de nombre dentro del mismo comercio si la política de normalización lo determina.

### RF-04 — Productos

- Crear, listar, consultar, editar y desactivar productos.
- Campos iniciales: nombre, SKU, categoría, precio de compra, precio de venta, stock mínimo y estado.
- El SKU debe ser único dentro de cada comercio.
- El stock actual no se modifica desde el formulario general de producto.
- Soportar búsqueda, filtros y paginación.

### RF-05 — Proveedores

- Crear, listar, editar y desactivar proveedores.
- Guardar datos de contacto comerciales mínimos.
- No recopilar datos que no sean necesarios para el funcionamiento del producto.

### RF-06 — Inventario

- Registrar entradas, salidas y ajustes autorizados.
- Guardar motivo, fecha, usuario y cantidad del movimiento.
- Mostrar stock actual e historial.
- Señalar productos cuyo stock sea igual o inferior al mínimo configurado.
- No permitir stock negativo salvo que una decisión de producto posterior lo autorice expresamente.

### RF-07 — Ventas

- Crear una venta con uno o más ítems.
- Validar disponibilidad de stock.
- Calcular importes en backend.
- Guardar el precio aplicado en cada ítem como dato histórico.
- Descontar inventario dentro de una transacción.
- Si la operación falla, no dejar venta parcial ni stock inconsistente.
- Registrar medio de pago como dato informativo; el MVP no procesa pagos.

### RF-08 — Gastos

- Registrar, listar, filtrar y consultar gastos.
- Campos: descripción, categoría, importe, fecha y usuario creador.
- No confundir gasto registrado con conciliación bancaria o contabilidad fiscal.

### RF-09 — Pedidos

- Crear pedidos con cliente opcional y uno o más ítems.
- Consultar pedidos y filtrar por estado y fecha.
- Estados iniciales propuestos: pendiente, en preparación, listo, entregado y cancelado.
- Definir y validar las transiciones permitidas en backend.
- Decidir antes de implementar si los pedidos reservan stock; propuesta inicial: no reservan stock hasta confirmar la venta.

### RF-10 — Dashboard y reportes

- Mostrar ventas del período.
- Mostrar gastos registrados del período.
- Mostrar productos con stock bajo.
- Mostrar pedidos pendientes.
- Mostrar productos más vendidos en un período.
- Las métricas deben documentar claramente cómo se calculan.

### RF-11 — Auditoría

- Registrar eventos críticos: cambios de stock, ventas, cambios de estado y cambios de permisos.
- Guardar actor, acción, entidad, identificador, fecha y metadatos mínimos.
- Los usuarios comunes no pueden editar ni borrar registros de auditoría.

## 2. Requisitos no funcionales

- Seguridad: autorización en backend y aislamiento entre comercios.
- Integridad: transacciones en operaciones que cambian stock y ventas.
- Usabilidad: formularios claros, mensajes de error comprensibles y diseño responsive.
- Rendimiento: filtros y paginación en endpoints de listados.
- Mantenibilidad: módulos separados y reglas de negocio fuera de los controladores HTTP.
- Calidad: pruebas unitarias para reglas críticas y pruebas de integración para flujos principales.
- Observabilidad: logs sin contraseñas, tokens ni datos sensibles innecesarios.
- Recuperación: copias de seguridad de base de datos y procedimiento de restauración probado antes de producción.
- Configuración: secretos en variables de entorno o gestor de secretos, nunca versionados.
- Accesibilidad básica: navegación por teclado, etiquetas de formulario y contraste suficiente.

## 3. Criterios de aceptación transversales

Una funcionalidad no se considera terminada si:

- No tiene validaciones y manejo de errores.
- No verifica permisos en backend.
- No tiene pruebas acordes al riesgo.
- No está integrada con el contrato acordado.
- No se ha probado el flujo completo en entorno local.
- No se actualizó la documentación relevante.
