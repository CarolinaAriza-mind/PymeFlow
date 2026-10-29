# 07 — Roadmap y estimación

## Supuesto de disponibilidad

Planificación de referencia: 30 horas semanales combinadas entre ambas desarrolladoras (por ejemplo, 3 horas diarias cada una, 5 días a la semana). La disponibilidad máxima indicada es de hasta 4 horas diarias cada una, pero se deja margen para estudio, coordinación y obligaciones personales.

## Estimación

- MVP funcional y desplegado: 16–24 semanas.
- MVP muy reducido: 10–12 semanas, con menor alcance.
- Escenario conservador: 6–8 meses.
- Producto más avanzado con integraciones: 8–12 meses o más.

Las etapas se superponen porque frontend y backend pueden trabajar en paralelo. Las estimaciones deben revisarse al final de cada sprint.

## Fases

### Fase 0 — Descubrimiento (1–2 semanas)

- Entrevistar 5–10 comercios.
- Validar problemas prioritarios.
- Definir alcance.
- Crear backlog y prototipo simple.

### Fase 1 — Fundaciones (2–3 semanas)

- Repositorio.
- Entornos.
- PostgreSQL y migraciones.
- Health check.
- Diseño inicial.
- CI básico si el equipo lo puede mantener.

### Fase 2 — Acceso y estructura de comercio (2–3 semanas)

- Registro/login.
- Membresías y roles.
- Aislamiento de datos.
- Layout y pantallas protegidas.

### Fase 3 — Productos e inventario (3–4 semanas)

- Categorías, productos, filtros.
- Movimientos de inventario.
- Stock bajo e historial.

### Fase 4 — Ventas y gastos (3–4 semanas)

- Ventas transaccionales.
- Descuento de stock.
- Gastos y filtros.

### Fase 5 — Pedidos, dashboard y reportes (3–4 semanas)

- Pedidos y estados.
- Indicadores.
- Reportes básicos.

### Fase 6 — Estabilización y piloto (2–3 semanas)

- Seguridad y pruebas.
- Copias de seguridad.
- Despliegue.
- Documentación.
- Prueba con comercios piloto.

## Hitos de producto

- Hito 1: frontend y backend se comunican.
- Hito 2: comercio y usuarios pueden acceder con permisos.
- Hito 3: productos e inventario funcionan.
- Hito 4: registrar una venta actualiza el stock correctamente.
- Hito 5: dashboard utiliza datos reales.
- Hito 6: piloto desplegado y feedback recogido.

## Política de alcance

No incorporar facturación electrónica, pagos online, múltiples depósitos, integraciones de terceros ni IA predictiva en el MVP salvo que la validación de usuarios demuestre que una de ellas es imprescindible.
