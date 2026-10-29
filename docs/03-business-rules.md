# 03 — Reglas de negocio

## Comercios y permisos

1. Cada dato operativo pertenece a un comercio.
2. Cada petición protegida debe comprobar que el usuario tiene acceso al comercio solicitado.
3. El frontend no es una frontera de seguridad.
4. Un usuario no puede leer ni modificar datos de otro comercio cambiando un ID en la URL.

## Productos

1. El SKU es único por comercio.
2. El producto puede desactivarse para preservar el historial.
3. Los precios deben validarse como decimales positivos o cero según la política acordada.
4. El stock se modifica mediante movimientos, no editando el producto directamente.

## Inventario

1. Cada cambio de stock crea un movimiento.
2. Los movimientos registran cantidad, tipo, motivo, fecha, usuario y comercio.
3. La cantidad se expresa como positiva junto con un tipo de movimiento explícito (entrada/salida/ajuste), o se define una convención única en el modelo; no mezclar convenciones.
4. Las operaciones concurrentes deben impedir que dos ventas consuman el mismo stock disponible.
5. El historial de movimientos no se borra para corregir errores; se registra un movimiento correctivo autorizado.

## Ventas

1. El backend obtiene los precios vigentes de la base de datos; no confía en el precio ni el total enviados por el navegador.
2. Cada ítem guarda una copia del precio aplicado y su subtotal.
3. Los cálculos monetarios utilizan un tipo decimal apropiado; no usar float para dinero.
4. La venta y los movimientos de stock se confirman en una única transacción.
5. Una venta no puede completarse si falta stock.
6. Cancelaciones o devoluciones futuras deberán revertir el inventario mediante movimientos explícitos y auditables.
7. El MVP registra el medio de pago, pero no procesa transacciones financieras.

## Pedidos

1. Un pedido no es necesariamente una venta.
2. En el MVP, crear un pedido no descuenta ni reserva stock.
3. El cambio de estado debe seguir una transición permitida.
4. La conversión de pedido a venta, si se incluye, debe ser una operación explícita y transaccional.

## Gastos e indicadores

1. Los gastos son registros de gestión interna y no equivalen por sí solos a contabilidad o declaración fiscal.
2. Las métricas deben especificar período, estados incluidos y fórmula.
3. Los reportes deben filtrar por comercio y respetar permisos.

## Auditoría

1. Las acciones críticas guardan quién, qué, cuándo y sobre qué entidad actuó.
2. No registrar secretos, contraseñas ni tokens en los logs.
