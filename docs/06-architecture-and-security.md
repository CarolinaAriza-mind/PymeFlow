# 06 — Arquitectura y seguridad

## Arquitectura lógica

Browser → Next.js frontend → FastAPI REST API → capa de servicios/repositorios → PostgreSQL.

## Principios

- El frontend presenta y valida para mejorar la experiencia; el backend vuelve a validar siempre.
- Los controladores HTTP no deben concentrar todas las reglas de negocio.
- Las operaciones críticas se implementan en servicios y transacciones.
- Cada consulta de datos operativos se limita al comercio autorizado.
- El contrato API es la fuente de verdad para la integración frontend/backend.

## Estructura sugerida

```text
pymeflow/
├── frontend/
│   ├── src/
│   │   ├── app/
│   │   ├── components/
│   │   ├── features/
│   │   ├── lib/
│   │   └── types/
│   └── package.json
├── backend/
│   ├── app/
│   │   ├── api/
│   │   │   └── v1/
│   │   ├── core/
│   │   ├── db/
│   │   ├── models/
│   │   ├── schemas/
│   │   ├── repositories/
│   │   ├── services/
│   │   └── main.py
│   ├── migrations/
│   ├── tests/
│   └── pyproject.toml
├── docs/
├── docker-compose.yml
└── README.md
```

## Seguridad mínima antes de un piloto real

- Hash de contraseñas con algoritmo de uso recomendado y biblioteca mantenida.
- No guardar contraseñas en texto plano.
- No guardar tokens ni secretos en el repositorio.
- Definir estrategia de autenticación antes de implementar. Evaluar cookies de sesión seguras HttpOnly/Secure/SameSite o tokens con almacenamiento seguro; evitar guardar tokens sensibles en localStorage sin evaluar riesgos.
- CORS limitado a los orígenes necesarios.
- Rate limiting en endpoints sensibles cuando corresponda.
- Validar autorización y pertenencia al comercio en cada operación.
- Proteger contra IDOR/BOLA: cambiar un ID no debe habilitar acceso a datos de otro comercio.
- No exponer errores internos ni secretos al cliente.
- Logs sin credenciales ni datos sensibles innecesarios.
- HTTPS en producción.
- Copias de seguridad y prueba documentada de restauración.
- Dependencias actualizadas y revisión de vulnerabilidades.
- Política de privacidad y términos antes de ofrecer el servicio públicamente.

## Testing

### Backend

- Unitarios para reglas de stock, cálculos y transiciones de estado.
- Integración para endpoints, base de datos y permisos.
- Casos de aislamiento entre dos comercios.
- Pruebas de concurrencia o bloqueo en operaciones de venta cuando corresponda.

### Frontend

- Tests de formularios y componentes críticos.
- Estados de carga, error, vacío y éxito.
- Pruebas de flujos de usuario principales.

### Flujos E2E prioritarios

1. Registrar comercio e iniciar sesión.
2. Crear categoría y producto.
3. Registrar entrada de inventario.
4. Crear una venta válida y verificar el descuento de stock.
5. Intentar vender más unidades de las disponibles y verificar que la operación falle sin cambios parciales.
6. Confirmar que un comercio no puede consultar datos de otro.
7. Registrar gasto y verificar el reporte del período.
