# 05 — Contrato inicial de API

Prefijo propuesto: `/api/v1`. La documentación interactiva estará disponible en el entorno de desarrollo mediante la ruta Swagger/OpenAPI que exponga FastAPI.

## Convenciones

- JSON para solicitudes y respuestas.
- Fechas en ISO 8601, almacenadas en UTC y mostradas en la zona horaria del comercio.
- Importes monetarios representados de forma decimal; evitar cálculos monetarios con float.
- Listados paginados.
- Errores con formato consistente.
- Todo endpoint protegido valida usuario, comercio y permisos.
- Las rutas y campos son propuestas iniciales; deben mantenerse sincronizados con los esquemas Pydantic y los tipos TypeScript.

## Endpoints propuestos

### Health

- `GET /api/v1/health`

### Auth

- `POST /api/v1/auth/register`
- `POST /api/v1/auth/login`
- `POST /api/v1/auth/logout` (si la estrategia de sesión lo requiere)
- `GET /api/v1/auth/me`

### Members

- `GET /api/v1/members`
- `POST /api/v1/members`
- `PATCH /api/v1/members/{membership_id}`
- `DELETE /api/v1/members/{membership_id}` (desactivar acceso, no borrar historial)

### Categories

- `GET /api/v1/categories`
- `POST /api/v1/categories`
- `GET /api/v1/categories/{category_id}`
- `PATCH /api/v1/categories/{category_id}`
- `DELETE /api/v1/categories/{category_id}` (desactivar)

### Products

- `GET /api/v1/products?search=&category_id=&low_stock=&page=&page_size=`
- `POST /api/v1/products`
- `GET /api/v1/products/{product_id}`
- `PATCH /api/v1/products/{product_id}`
- `DELETE /api/v1/products/{product_id}` (desactivar)

### Suppliers

- `GET /api/v1/suppliers`
- `POST /api/v1/suppliers`
- `GET /api/v1/suppliers/{supplier_id}`
- `PATCH /api/v1/suppliers/{supplier_id}`
- `DELETE /api/v1/suppliers/{supplier_id}`

### Inventory

- `GET /api/v1/inventory/movements?product_id=&movement_type=&from=&to=&page=`
- `POST /api/v1/inventory/movements`
- `GET /api/v1/inventory/low-stock`

### Sales

- `GET /api/v1/sales?from=&to=&status=&page=`
- `POST /api/v1/sales`
- `GET /api/v1/sales/{sale_id}`
- Cancelación: definir endpoint explícito y permisos antes de implementarlo.

### Expenses

- `GET /api/v1/expenses?from=&to=&category=&page=`
- `POST /api/v1/expenses`
- `GET /api/v1/expenses/{expense_id}`
- `PATCH /api/v1/expenses/{expense_id}` (definir política de edición y auditoría)

### Orders

- `GET /api/v1/orders?status=&from=&to=&page=`
- `POST /api/v1/orders`
- `GET /api/v1/orders/{order_id}`
- `PATCH /api/v1/orders/{order_id}/status`

### Dashboard and reports

- `GET /api/v1/dashboard/summary?from=&to=`
- `GET /api/v1/reports/sales?from=&to=&group_by=day`
- `GET /api/v1/reports/top-products?from=&to=&limit=`

## Ejemplo de error

```json
{
  "error": {
    "code": "INSUFFICIENT_STOCK",
    "message": "No hay stock suficiente para completar la venta.",
    "details": []
  }
}
```

## Contrato de creación de producto (ejemplo)

Request:

```json
{
  "name": "Yerba mate",
  "sku": "YER-001",
  "category_id": "ID_DE_CATEGORIA",
  "purchase_price": "1800.00",
  "sale_price": "2500.00",
  "initial_stock": "20",
  "min_stock": "5"
}
```

El backend valida el producto y registra el stock inicial como movimiento. El cliente no debe enviar `current_stock` en actualizaciones ordinarias. El formato de IDs se ajustará a la decisión UUID/BIGINT.
