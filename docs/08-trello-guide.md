# 08 — Guía de Trello para PymeFlow

## 1. Crear el tablero

Nombre: **PymeFlow — Desarrollo del MVP**

Descripción sugerida:

> Desarrollo colaborativo de PymeFlow, una aplicación web de gestión para pequeños comercios. Frontend Next.js/TypeScript, backend Python/FastAPI y PostgreSQL. Objetivo: construir, probar y validar un MVP en 16–24 semanas.

## 2. Listas del tablero

1. **📥 Backlog** — ideas y tareas aprobadas para hacer más adelante.
2. **🧭 Próximo sprint** — tareas seleccionadas para el sprint actual.
3. **🛠️ En progreso** — tareas activas; limitar a 1–2 tareas por persona.
4. **👀 Revisión de código** — listas para revisión o feedback.
5. **🔗 Integración / QA** — tareas que necesitan prueba conjunta.
6. **⛔ Bloqueado** — tareas que no pueden avanzar; explicar el bloqueo en comentarios.
7. **✅ Hecho** — tareas aceptadas según sus criterios.

No crear listas por persona. Usar miembros y etiquetas para distinguir responsables y áreas.

## 3. Etiquetas

- `BACKEND · Python`
- `FRONTEND · Next.js`
- `DATABASE`
- `TESTING · QA`
- `DOCS`
- `SECURITY`
- `PRODUCT · Discovery`
- `BUG`
- `BLOCKER`

## 4. Campos recomendados en cada tarjeta

Título: verbo + resultado concreto. Ejemplo: `Crear endpoint para listar productos`.

Descripción:

- **Objetivo:** qué problema resuelve.
- **Contexto:** por qué hace falta.
- **Alcance:** qué incluye y qué queda fuera.
- **Criterios de aceptación:** lista comprobable.
- **Dependencias:** otras tarjetas o decisiones necesarias.
- **Documentación:** ruta del archivo relevante.
- **Pruebas:** cómo verificar que funciona.

Cada tarjeta debe tener:

- Una persona responsable principal.
- Una fecha objetivo cuando sea útil.
- Etiqueta de área.
- Estimación en puntos o tamaño (S/M/L), acordada por el equipo.
- Checklist si contiene varios pasos independientes.

## 5. Flujo de trabajo

1. Acordar el alcance del sprint semanal.
2. Seleccionar tareas que puedan terminarse en una semana.
3. Confirmar dependencias entre frontend y backend.
4. Mover una tarjeta a En progreso al comenzar.
5. Adjuntar PR o enlace de GitHub cuando exista.
6. Pasar a Revisión de código.
7. Probar la integración en Integración / QA.
8. Mover a Hecho únicamente cuando cumpla los criterios de aceptación.
9. Revisar el sprint al final de la semana: completado, pendiente, bloqueos y aprendizaje.

## 6. Definition of Ready

Una tarea está lista para comenzar cuando:

- Tiene objetivo claro.
- Tiene criterios de aceptación.
- Tiene responsable.
- Tiene dependencias identificadas.
- El contrato API o diseño necesario está acordado.
- El alcance cabe razonablemente en el sprint.

## 7. Definition of Done

Una tarea está terminada cuando:

- El código está integrado mediante pull request.
- Las pruebas relevantes pasan.
- Se validan permisos y errores según corresponda.
- No quedan secretos en el código.
- La integración funciona localmente.
- La documentación se actualizó.
- La otra desarrolladora pudo revisar el resultado.

## 8. Ritmo recomendado

- Planificación semanal: 30 minutos.
- Check-in breve por día trabajado: 5–10 minutos por chat o llamada.
- Revisión/demostración semanal: 20–30 minutos.
- Retrospectiva semanal: 10–15 minutos.

Preguntas de retrospectiva:

- ¿Qué salió bien?
- ¿Qué nos bloqueó?
- ¿Qué aprendimos?
- ¿Qué cambiaremos la semana próxima?

## 9. Integración con GitHub

Convención de ramas:

- `feat/backend-products`
- `feat/frontend-products`
- `fix/backend-stock-validation`
- `docs/api-contract`

Convención de commits sugerida:

- `feat: add product creation endpoint`
- `fix: prevent sale with insufficient stock`
- `test: cover inventory movement rules`
- `docs: update product API contract`

En la tarjeta de Trello agregar el enlace a la rama o pull request. No usar Trello como reemplazo de GitHub para revisar código.
