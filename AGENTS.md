# STATUX — Plataforma de Bots y Apps en Tiempo Real para Negocios Locales ⚡

Este repositorio contiene la arquitectura, código y documentación de **STATUX** (*"El estado de tu negocio, en tiempo real"*), una empresa orientada a **aplicaciones y bots automatizados para negocios locales (Restaurantes, Talleres mecánicos, Barberías y Supermercados)**.

---

## 1. Visión y Propósito
El objetivo de la plataforma es eliminar la incertidumbre del cliente ("¿cómo va mi pedido/carro/turno?") y automatizar la atención repetitiva para el dueño del negocio mediante:
1. **Canal de Comunicación Principal:** WhatsApp (Cloud API / Webhooks) sin obligar al cliente final a descargar aplicaciones pesadas.
2. **Visualización en Vivo (PWA / Web Ligera):** Enlaces rápidos generados por el bot donde el cliente puede ver una barra de progreso interactiva en tiempo real.
3. **Panel de Control Operativo (KDS / Admin Panel):** Interfaz táctil, rápida y amigable con botones grandes para que el personal (cocineros, mecánicos, barberos, dependientes) cambie el estado en un solo toque.

---

## 2. Regla de Oro Pedagógica: Explicaciones Nivel Novato / Modo Estudio
- **Pedagogía Primero:** Todas las explicaciones técnicas, arquitectónicas y de código deben hacerse **a nivel principiante**, utilizando analogías de la vida real (metáforas cotidianas).
- **Estructura Didáctica:**
  1. ¿Qué es en una sola frase sencilla?
  2. Analogía del mundo real.
  3. ¿Qué problema resuelve?
  4. Mini resumen para estudiar (*Flashcard mental*).
- **Prohibido el lenguaje técnico inaccesible:** Ningún término técnico o sigla (ej. CQRS, Docker, Webhook, ORM, Redis) puede usarse sin explicar qué significa de forma clara y visual.
- **Objetivo:** Que el usuario no solo reciba código, sino que **aprenda los conceptos a fondo y desarrolle criterio técnico sólido**.

---

## 3. Principios de Arquitectura

- **Núcleo Común (Core Engine):** La lógica de estados, cola de notificaciones, registro de clientes y webhooks de mensajería debe ser modular y agnóstica del nicho.
- **Backend Stack:** Python 3.12+ con **FastAPI**, **Pydantic v2**, estructurado bajo **Vertical Slice Architecture + CQRS** para independizar comandos (escrituras) de consultas (lecturas).
- **Procesamiento Asíncrono:** Redis + Worker en segundo plano para envío de WhatsApp sin bloquear la interfaz táctil del empleado.
- **Contenedores:** Docker y Docker Compose para orquestar la API, base de datos (PostgreSQL), Redis y Worker.
- **Verticales Adaptables:** Cada vertical (Restaurante, Taller, Barbería, Supermercado) hereda del motor de estados pero define:
  - Sus propios estados (ej. `[EN_HORNO]` vs `[EN_DIAGNOSTICO]` vs `[TURNO_SIGUIENTE]`).
  - Sus propias plantillas de mensajes y botones interactivos.
  - Sus campos de datos personalizados (ej. `placa_vehiculo`, `numero_mesa`, `barbero_asignado`).
- **Mobile-First & Touch-Friendly:** Las pantallas del personal deben funcionar perfectamente en tablets de cocina o teléfonos en el mostrador.
- **Cero Fricción para el Cliente Final:** Toda interacción debe poder iniciarse por código QR físico o mensaje de WhatsApp.

---

## 3. Estándares de Mensajería (WhatsApp)
- Mensajes directos, cordiales y con tono profesional adaptado a la marca del negocio.
- Uso de emojis claros para identificar visualmente cada estado (ej. 👨‍🍳 En cocina, 🍕 En el horno, 🛵 En camino, 🚗 En diagnóstico, ✂️ Tu turno).
- Siempre incluir un botón o enlace de acción claro cuando se requiera respuesta del usuario.

---

## 4. Gestión de Progreso y Sprints
- Todas las tareas se organizan en el documento raíz [`SPRINT.md`](file:///Users/cristiancastro/David-Desk/empresa/SPRINT.md).
- Cada vez que se empiece o se complete una tarea técnica, el agente debe actualizar inmediatamente el estado de las casillas (`[ ]` -> `[⏳]` -> `[x]`) y la barra de progreso en `SPRINT.md`.

---

## 5. Estándares de Portafolio Profesional (SDET & Pipeline Developer)
- **Código Testeable por Diseño:** Todo endpoint y comando debe poder probarse de forma aislada sin dependencias duras (usando inyección de dependencias y Mocks).
- **Pruebas Automatizadas (Pytest):** Cada funcionalidad del backend debe contar con su correspondiente prueba automatizada unitaria o de integración.
- **Enfoque de Pipeline:** La orquestación con Docker Compose, colas de Redis y workers debe documentarse de forma que demuestre dominio de flujos de trabajo automatizados para entrevistas laborales.

---

## 6. Estándares de Git (Conventional Commits)
- Todo commit en este repositorio debe seguir estrictamente la convención: `<tipo>(<alcance>): <descripción>`.
- Tipos válidos: `feat:`, `fix:`, `test:`, `ci:`, `docs:`, `refactor:`, `chore:`.
- Ejemplo: `feat(orders): implementar comando para transicion de estado a en_horno`.
- Plantilla disponible en [`.gitmessage`](file:///Users/cristiancastro/David-Desk/empresa/.gitmessage).

---

## 7. Protocolo de Monitoreo y Diagnóstico (Regla de los 63 Segundos)
- Si cualquier tarea, ejecución de comando o proceso tarda **63 segundos o más** en responder, el asistente debe emitir inmediatamente un **Informe de Diagnóstico Estructurado (RCA - Root Cause Analysis)**.
- El informe debe detallar: qué se estaba ejecutando, el punto exacto de lentitud, la causa raíz explicada de forma pedagógica y la solución más eficiente para resolverlo de inmediato.

---

## 8. Directorio de Skills Disponibles (`.agents/skills/`)
- `git-commit-standards`: Nomenclatura Conventional Commits, plantillas de confirmación y buenas prácticas de Git.
- `sales-pitch-master`: Ventas B2B puerta a puerta, oratoria persuasiva, manejo de objeciones, marketing local y simulador de entrenamiento para hablar en público.
- `brand-strategist`: Estrategia de marca, naming, validación de nombres, presencia en internet y dominios.
- `task-watchdog`: Supervisión de ejecuciones y emisión de informes de diagnóstico ante pausas de 63 segundos.
- `sdet-pipeline-mentor`: Guía pedagógica para rol laboral de QA Automation / SDET y Pipeline/Render TD, preparación de entrevistas y pruebas automatizadas.
- `mentor-educativo`: Guía de pedagogía, explicaciones a nivel principiante y analogías de la vida real.
- `sprint-manager`: Control de tareas por fases, historias de usuario y sincronización de `SPRINT.md`.
- `backend-architecture`: Stack de Python, FastAPI, Docker Compose, Redis y patrón Vertical Slice + CQRS.
- `bot-flow-architect`: Diseño y estructuración de flujos conversacionales, plantillas y árboles de decisión.
- `order-status-tracker`: Motor universal de eventos y estados en tiempo real con pantalla de seguimiento para el cliente.
- `whatsapp-engine`: Integración técnica de WhatsApp Cloud API, webhooks y colas de entrega.
- `verticals-playbook`: Catálogo de flujos específicos, esquemas de datos y mensajes para Restaurantes, Talleres, Barberías y Supermercados.
