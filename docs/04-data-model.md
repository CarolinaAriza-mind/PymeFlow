# 04 — Modelo de datos inicial

Este es un modelo conceptual. La definición física final debe revisarse antes de crear migraciones.

## Entidades principales

### businesses

- id (UUID o BIGINT; elegir una estrategia)
- name
- business_type (opcional)
- timezone
- created_at
- updated_at
- is_active

### users

- id
- full_name
- email (normalizado; unicidad global si el diseño usa una cuenta por persona)
- password_hash (nunca guardar contraseña en texto plano)
- is_active
- created_at
- updated_at

### business_memberships

- id
- business_id (FK)
- user_id (FK)
- role (ADMIN, EMPLOYEE)
- status
- created_at
- Unique(business_id, user_id)

### categories

- id
- business_id (FK)
- name
- description (opcional)
- is_active
- created_at
- Unique(business_id, normalized_name)

### products

- id
- business_id (FK)
- category_id (FK nullable según decisión)
- name
- sku
- purchase_price (NUMERIC/DECIMAL)
- sale_price (NUMERIC/DECIMAL)
- current_stock (NUMERIC/DECIMAL; unidad entera o fraccionaria según productos)
- min_stock
- is_active
- created_at
- updated_at
- Unique(business_id, sku)

### suppliers

- id
- business_id (FK)
- name
- phone (opcional)
- email (opcional)
- notes (opcional)
- is_active
- created_at
- updated_at

### product_suppliers

- product_id (FK)
- supplier_id (FK)
- supplier_sku (opcional)
- last_purchase_price (opcional)
- Unique(product_id, supplier_id)

### inventory_movements

- id
- business_id (FK)
- product_id (FK)
- movement_type (ENTRY, SALE, ADJUSTMENT_IN, ADJUSTMENT_OUT, RETURN, OTHER según alcance)
- quantity (NUMERIC/DECIMAL positivo)
- reason
- reference_type (opcional)
- reference_id (opcional)
- created_by_user_id (FK)
- created_at

### customers

- id
- business_id (FK)
- name
- phone (opcional)
- email (opcional)
- created_at
- is_active

### sales

- id
- business_id (FK)
- sale_number
- status (CONFIRMED, CANCELLED; política por definir)
- subtotal
- discount_total (opcional)
- total
- payment_method (informativo)
- created_by_user_id (FK)
- created_at
- Unique(business_id, sale_number)

### sale_items

- id
- sale_id (FK)
- product_id (FK)
- product_name_snapshot
- quantity
- unit_price
- subtotal

### expenses

- id
- business_id (FK)
- category
- description
- amount
- expense_date
- created_by_user_id (FK)
- created_at

### orders

- id
- business_id (FK)
- customer_id (FK nullable)
- status
- notes (opcional)
- total
- created_by_user_id (FK)
- created_at
- updated_at

### order_items

- id
- order_id (FK)
- product_id (FK)
- product_name_snapshot
- quantity
- unit_price
- subtotal

### audit_logs

- id
- business_id (FK)
- actor_user_id (FK nullable para eventos de sistema)
- action
- entity_type
- entity_id
- metadata (JSONB, sin secretos)
- created_at

## Relaciones

- businesses 1:N business_memberships
- users 1:N business_memberships
- businesses 1:N categories, products, suppliers, customers, sales, expenses, orders, inventory_movements, audit_logs
- categories 1:N products
- products N:M suppliers mediante product_suppliers
- sales 1:N sale_items
- orders 1:N order_items
- products 1:N inventory_movements

## Decisiones que deben cerrarse antes de implementar

1. UUID o BIGINT para IDs.
2. Si un usuario puede pertenecer a varios comercios (modelo recomendado: sí, mediante business_memberships).
3. Si se permiten productos fraccionarios (por peso/volumen).
4. Si el stock actual se almacena como valor derivado/mantenido o se calcula desde movimientos. Para MVP, puede mantenerse un saldo en products actualizado transaccionalmente y auditarse con movimientos.
5. Convención de movimientos y ajustes.
6. Política de cancelación y devolución de ventas.
7. Política de eliminación lógica y retención de datos.
8. Si pedidos se convierten en ventas en el MVP.
