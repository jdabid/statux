---
name: backend-architecture
description: >-
  Estandariza el stack tecnológico de backend (Python, FastAPI, Docker Compose, Redis, PostgreSQL) bajo el patrón Vertical Slice Architecture + CQRS para flujos de alta concurrencia, APIs y tareas en segundo plano.
---

# Backend Architecture Skill (Python + Vertical Slice + CQRS)

Esta habilidad define la estructura de carpetas, convenciones de diseño y patrones de implementación para el backend de la plataforma.

---

## 1. Patrón Arquitectónico: Vertical Slice + CQRS

En lugar de capas horizontales tradicionales (`controllers/`, `services/`, `repositories/`), el código se organiza por **capacidades de negocio (Features)**. Cada Feature encapsula su propio transporte, validación, lógica de comando o consulta y persistencia.

### Estructura de Directorios Recomendada:

```text
backend/
├── app/
│   ├── core/                      # Configuración transversal
│   │   ├── config.py              # Variables de entorno (Pydantic Settings)
│   │   ├── database.py            # Sesión async de PostgreSQL (SQLAlchemy / SQLModel)
│   │   ├── redis.py               # Pool de conexiones Redis
│   │   └── security.py            # Hashing, tokens de seguimiento y JWT
│   │
│   ├── features/                  # Vertical Slices (Agrupadas por dominio)
│   │   ├── orders/                # Gestión de órdenes y estados
│   │   │   ├── commands/          # Mutaciones (Create, UpdateStatus, Cancel)
│   │   │   │   ├── create_order.py
│   │   │   │   └── update_order_status.py
│   │   │   ├── queries/           # Lecturas optimizadas (GetById, ListActive)
│   │   │   │   ├── get_order_by_token.py
│   │   │   │   └── list_kds_orders.py
│   │   │   └── router.py          # Endpoints FastAPI correspondientes a orders
│   │   │
│   │   ├── whatsapp/              # Slice de mensajería y webhooks
│   │   │   ├── commands/
│   │   │   │   ├── handle_incoming_webhook.py
│   │   │   │   └── queue_notification.py
│   │   │   └── router.py
│   │   │
│   │   └── tenants/               # Slice de gestión de negocios y configuraciones
│   │
│   ├── workers/                   # Tareas en segundo plano (Background Tasks)
│   │   ├── worker.py              # Worker process (ARQ o Celery)
│   │   └── tasks/
│   │       └── send_whatsapp_task.py
│   │
│   └── main.py                    # Entrypoint de FastAPI y montaje de routers
│
├── Dockerfile
├── docker-compose.yml
└── requirements.txt (o pyproject.toml / uv)
```

---

## 2. Implementación de un Slice (Ejemplo CQRS)

### Command: Actualizar Estado del Pedido (`update_order_status.py`)
```python
from pydantic import BaseModel
from app.workers.worker import enqueue_whatsapp_notification

# 1. DTO de entrada (Command)
class UpdateOrderStatusCommand(BaseModel):
    order_id: str
    new_status: str
    notes: str | None = None

# 2. Handler del comando
async def handle_update_order_status(cmd: UpdateOrderStatusCommand, db, redis):
    # a. Validar transición de estado
    order = await db.get_order(cmd.order_id)
    order.transition_to(cmd.new_status)
    await db.commit()

    # b. Notificar en tiempo real a la Web (Redis Pub/Sub -> WebSockets)
    await redis.publish(f"order:{order.token}", order.new_status)

    # c. Encolar mensaje de WhatsApp sin bloquear la respuesta HTTP
    await enqueue_whatsapp_notification(
        phone=order.customer_phone,
        status=order.new_status,
        tracking_token=order.token
    )

    return {"success": True, "status": order.new_status}
```

### Query: Obtener Estado para el Comensal (`get_order_by_token.py`)
```python
# Consulta directa, ultra rápida, sin lógica de negocio pesada
async def handle_get_order_status(token: str, db):
    # Consulta directa optimizada a la DB o lectura directa de Redis caché
    return await db.fetch_order_status_summary(token)
```

---

## 3. Docker & Docker Compose Estándar

El entorno de ejecución contiene:
1. **`api`**: Servicio FastAPI con Uvicorn (hot-reload en dev).
2. **`worker`**: Proceso en segundo plano para envío de WhatsApp y retries.
3. **`db`**: PostgreSQL 16 con volumen persistente.
4. **`redis`**: Redis Alpine para colas, Pub/Sub de WebSockets y caché.
