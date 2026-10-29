# PymeFlow

**Sistema web de gestión para pequeños comercios que venden productos físicos.**

## Objetivo

Centralizar productos, inventario, ventas, gastos, pedidos y reportes en una aplicación web sencilla y confiable.

## Stack acordado

- Frontend: Next.js, React, TypeScript, Tailwind CSS.
- Backend: Python, FastAPI, Pydantic, SQLAlchemy.
- Base de datos: PostgreSQL.
- Migraciones: Alembic.
- Testing: pytest (backend); Vitest + React Testing Library (frontend).
- Documentación API: OpenAPI/Swagger generado por FastAPI.
- Control de versiones: Git + GitHub.
- Gestión de tareas: Trello.
- Contenedores locales: Docker Compose, incorporado cuando la configuración base esté clara.

## Alcance del MVP

1. Registro del comercio, inicio de sesión y permisos.
2. Productos y categorías.
3. Inventario y movimientos.
4. Proveedores.
5. Ventas.
6. Gastos.
7. Pedidos.
8. Dashboard y reportes básicos.
9. Auditoría de operaciones relevantes.
10. Despliegue, documentación y pruebas.

## Fuera de alcance del MVP

- Facturación electrónica ARCA.
- Procesamiento de pagos online.
- Integraciones con Mercado Libre, Tiendanube o WhatsApp.
- Multi-sucursal y multi-depósito.
- Aplicación móvil nativa.
- IA predictiva.
- Contabilidad avanzada.

## Supuestos por confirmar

- El primer segmento será comercios minoristas con productos físicos.
- Se comienza con un depósito por comercio.
- La venta registra el medio de pago, pero no procesa el cobro.
- Se apunta a un MVP comercializable en 16–24 semanas, con 30 horas de equipo por semana como planificación de referencia.
- Los roles iniciales serán Administrador/Dueño y Empleado.
- La autenticación y el mecanismo de sesión se definirán antes de implementar login; se priorizará seguridad y simplicidad.

## Documentos

- `01-product-brief.md`: problema, usuarios, objetivos y alcance.
- `02-requirements.md`: requisitos funcionales y no funcionales.
- `03-business-rules.md`: reglas de negocio.
- `04-data-model.md`: entidades y relaciones iniciales.
- `05-api-contract.md`: endpoints propuestos.
- `06-architecture-and-security.md`: arquitectura, estructura y seguridad.
- `07-roadmap.md`: plan de trabajo.
- `08-trello-guide.md`: configuración profesional de Trello.
- `trello_backlog.csv`: backlog inicial para cargar/recrear tarjetas.
