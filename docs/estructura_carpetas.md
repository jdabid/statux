# Propuesta de Estructura de Carpetas del Proyecto 📁

Este documento explica cómo estará organizado cada rincón de nuestro proyecto, qué función cumple cada carpeta y cómo se conectan entre sí.

---

## 1. Explicación Didáctica (Para Estudiar)

- **¿Qué es una estructura de carpetas limpia en una frase?**  
  Es como tener un taller de herramientas bien rotulado: cada llave, tuerca y destornillador tiene su propio cajón etiquetado, para no perder tiempo buscando dónde va cada cosa.
- **La Analogía de la Vida Real:**  
  Imagina la casa de un restaurante:
  - **`backend/` (La Cocina Oculta):** Donde se preparan los pedidos, se lavan las ollas y se guardan las recetas secretas en la caja fuerte.
  - **`frontend/` (El Comedor y el Mostrador):** Lo que ve el cliente y el cajero (mesas bonitas, cartas de menú y pantallas).
  - **`docker-compose.yml` (El Interruptor General de Luz):** Con un solo botón prendes las luces de la cocina, las neveras y el comedor al mismo tiempo.
- **¿Qué problema resuelve?:** Si metemos todo en un solo archivo gigante o en carpetas desordenadas, hacer cualquier cambio pequeño se vuelve una pesadilla y se rompe el sistema sin saber por qué.

---

## 2. Mapa Visual del Repositorio

```text
empresa/
├── AGENTS.md                  # Reglas del proyecto y estándares de calidad
├── README.md                  # Portada y visión general de la plataforma
├── SPRINT.md                  # Tablero de control del Sprint actual (Progreso vivo)
├── docker-compose.yml         # Orquestador: Enciende API + Worker + Base de Datos + Redis
│
├── .agents/                   # Cerebro del Asistente de IA (Skills especializados)
│   └── skills/
│       ├── mentor-educativo/      # Modo novato y explicaciones con analogías
│       ├── sprint-manager/        # Control de tareas y actualización de SPRINT.md
│       ├── backend-architecture/  # Python, FastAPI, Docker y CQRS
│       ├── bot-flow-architect/    # Diseño de flujos de WhatsApp
│       ├── order-status-tracker/  # Motor de estados y barra de progreso
│       ├── whatsapp-engine/       # Conectores y Webhooks de WhatsApp
│       └── verticals-playbook/    # Reglas para Restaurantes, Talleres, etc.
│
├── docs/                      # Documentación y guías de estudio
│   └── estructura_carpetas.md # Este documento
│
├── backend/                   # 🐍 Servidor Python (FastAPI + Vertical Slice + CQRS)
│   ├── Dockerfile             # La receta para empaquetar el backend en una "lonchera"
│   ├── requirements.txt       # Lista de ingredientes/librerías de Python
│   └── app/
│       ├── main.py            # Puerta de entrada del servidor
│       ├── core/              # Herramientas universales (Base de datos, Redis, Config)
│       │   ├── config.py      # Contraseñas y variables de entorno
│       │   ├── database.py    # Conexión con PostgreSQL
│       │   └── redis.py       # Conexión con la memoria rápida de Redis
│       │
│       ├── features/          # 🍕 Los Vertical Slices (Agrupados por función)
│       │   ├── orders/        # Todo lo relacionado con órdenes/pedidos
│       │   │   ├── router.py  # Rutas HTTP (URLs a las que se hace clic)
│       │   │   ├── commands/  # Acciones que CAMBIAN datos (Crear orden, Cambiar estado)
│       │   │   │   ├── create_order.py
│       │   │   │   └── update_order_status.py
│       │   │   └── queries/   # Acciones que SOLO LEEN datos (Ver estado para el comensal)
│       │   │       ├── get_order_by_token.py
│       │   │       └── list_kds_orders.py
│       │   │
│       │   └── whatsapp/      # Todo lo relacionado con enviar y recibir mensajes
│       │       ├── router.py
│       │       ├── commands/
│       │       │   ├── handle_webhook.py
│       │       │   └── send_status_notification.py
│       │       └── services/
│       │           └── meta_api.py
│       │
│       └── workers/           # 🧑‍🍳 Los ayudantes en segundo plano
│           ├── worker.py      # Proceso que atiende las tareas de la cola
│           └── tasks/         # Tareas específicas (ej. mandar WhatsApp sin frenar la cocina)
│               └── whatsapp_tasks.py
│
└── frontend/                  # 🎨 Pantallas visuales interactivas
    ├── kds/                   # Pantalla táctil de cocina / empleado (Kitchen Display System)
    └── tracking/              # Pantalla web ligera para el cliente con barra de progreso
```

---

## 3. ¿Por qué separamos `commands/` y `queries/` en cada Slice?

| Carpeta | Nombre CQRS | ¿Qué hace? | Analogía |
| :--- | :--- | :--- | :--- |
| **`commands/`** | Comandos (Escritura) | Crea o altera información (guarda en base de datos, descuenta inventario, dispara alertas). | El cocinero metiendo la pizza al horno y marcando la comanda. |
| **`queries/`** | Consultas (Lectura) | Solo devuelve datos para mostrarlos en pantalla (no altera nada). Es ultra veloz. | El cliente mirando la televisión de la sala de espera para ver si su número ya salió. |

---

## 4. 💡 Flashcard para Estudiar:
> **Regla de oro de esta estructura:**  
> Si mañana queremos agregar la vertical de **Talleres Mecánicos**, no tocamos la carpeta de restaurantes. Creamos un nuevo módulo o slice adaptado, compartiendo el mismo motor de estados y el mismo worker de WhatsApp.
