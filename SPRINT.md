# 📋 STATUX — Tablero de Control de Sprints (Sprint Board)

Este documento es el **mapa de vuelo en tiempo real** de **STATUX**. Se actualiza automáticamente cada vez que completamos una tarea para que siempre sepamos qué se ha hecho, qué se está haciendo y qué sigue.

---

## 🏃 Sprint Actual: Sprint 1 — Cimientos del Backend y MVP de STATUX Gastro (Restaurantes)

* **Meta del Sprint:** Tener el entorno de desarrollo funcionando en Docker (FastAPI + PostgreSQL + Redis), con la estructura de carpetas lista y el primer flujo de pedido de restaurante funcionando (cambio de estado de cocina y notificación simulada).
* **Estado:** `[⏳] EN PROCESO`
* **Progreso:** `15%` `[■■□□□□□□□□]`

---

### 📝 Lista de Tareas del Sprint 1

#### Fase 1: Preparación y Arquitectura Base
- [x] **Tarea 1.1:** Definir visión del negocio, reglas y habilidades especializadas (`.agents/skills`).
- [x] **Tarea 1.2:** Diseñar y documentar la estructura de carpetas didáctica ([`docs/estructura_carpetas.md`](file:///Users/cristiancastro/David-Desk/empresa/docs/estructura_carpetas.md)).
- [x] **Tarea 1.3:** Crear el sistema de gestión por Sprints (`SPRINT.md` y skill `sprint-manager`).
- [ ] **Tarea 1.4:** Crear archivo `docker-compose.yml` base (FastAPI + PostgreSQL 16 + Redis 7 + Worker).
- [ ] **Tarea 1.5:** Crear `Dockerfile` y `requirements.txt` del backend en Python 3.12.

#### Fase 2: El Núcleo de la API (Python + FastAPI)
- [ ] **Tarea 2.1:** Configurar la conexión a la base de datos (PostgreSQL) y Redis en `backend/app/core/`.
- [ ] **Tarea 2.2:** Crear el modelo de datos de **Órdenes y Estados** (Pendiente, En Preparación, En el Horno, Listo).
- [ ] **Tarea 2.3:** Implementar el primer **Command** CQRS: `create_order.py` (Crear un nuevo pedido con token de seguimiento).
- [ ] **Tarea 2.4:** Implementar el segundo **Command** CQRS: `update_order_status.py` (Cambiar de estado y encolar notificación).
- [ ] **Tarea 2.5:** Implementar la primera **Query** CQRS: `get_order_by_token.py` (Leer el estado en tiempo real para el cliente).

#### Fase 3: Procesamiento en Segundo Plano (Worker & Mensajería)
- [ ] **Tarea 3.1:** Configurar el Worker con Redis (ayudante en segundo plano para no congelar la pantalla de cocina).
- [ ] **Tarea 3.2:** Implementar la tarea simulada de WhatsApp (`whatsapp_tasks.py`) con logs visuales de mensajes enviados.

#### Fase 4: Pruebas y Validación del MVP (Enfoque SDET)
- [ ] **Tarea 4.1:** Levantar el entorno con `docker compose up` y verificar que todos los contenedores respondan con salud.
- [ ] **Tarea 4.2:** Probar el flujo completo: Crear pedido $\rightarrow$ Pasar a "En el horno" $\rightarrow$ Pasar a "Listo" $\rightarrow$ Verificar que el cliente ve la barra de progreso avanzar.
- [ ] **Tarea 4.3:** Crear la suite de **Pruebas Automatizadas con Pytest** (`tests/`) validando comandos, queries y mocks de WhatsApp (Pieza clave de portafolio para QA Automation / SDET).

---

## 🔮 Backlog de Futuros Sprints (Próximos Pasos)

- **Sprint 2:** Pantalla visual táctil para la cocina (KDS) + Pantalla web animada para el comensal (*STATUX Live*).
- **Sprint 3:** Conexión real con Meta WhatsApp Cloud API y Webhooks entrantes.
- **Sprint 4:** Adaptación a **STATUX Auto** (Talleres Mecánicos: Check-in con fotos y aprobación de presupuestos por WhatsApp).
- **Sprint 5:** Adaptación a **STATUX Barber** (Barberías: Turnos inteligentes y recordatorios anti-inasistencias).
- **Sprint 6:** Adaptación a **STATUX Market** (Supermercados: Catálogo y pedidos express).
