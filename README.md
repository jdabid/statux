# STATUX ⚡
### *"El estado de tu negocio, en tiempo real"*

Plataforma modular de automatización, bots conversacionales (WhatsApp) y seguimiento de estados en tiempo real para negocios de proximidad.

---

## 🎯 Verticals de STATUX
1. **STATUX Gastro (Restaurantes):** Seguimiento de pedidos en vivo (*Cocina $\rightarrow$ En el Horno $\rightarrow$ Listo para servir*).
2. **STATUX Auto (Talleres Mecánicos):** Check-in de vehículos, diagnóstico, aprobación de presupuestos por WhatsApp y entrega.
3. **STATUX Barber (Barberías y Salones):** Turnos inteligentes, alertas de proximidad y eliminación de inasistencias.
4. **STATUX Market (Supermercados):** Pedidos rápidos, picking, empaque y delivery express.

---

## 🧠 Habilidades Especializadas (Skills del Agente)
Este repositorio cuenta con un sistema de agentes y habilidades configurados en `.agents/skills/`:

| Skill | Función |
| :--- | :--- |
| [`bot-flow-architect`](file:///.agents/skills/bot-flow-architect/SKILL.md) | Diseño de flujos conversacionales y árboles de decisión en WhatsApp. |
| [`order-status-tracker`](file:///.agents/skills/order-status-tracker/SKILL.md) | Motor de estados finitos (FSM), KDS para empleados y vista web en vivo para clientes. |
| [`whatsapp-engine`](file:///.agents/skills/whatsapp-engine/SKILL.md) | Integración con APIs de WhatsApp, webhooks, plantillas y simulador local. |
| [`verticals-playbook`](file:///.agents/skills/verticals-playbook/SKILL.md) | Reglas de negocio, copys y modelos de datos específicos por sector. |

---

## 📐 Estructura del Proyecto
```text
empresa/
├── AGENTS.md                  # Reglas del proyecto y estándares de desarrollo
├── README.md                  # Descripción general y roadmap
├── .agents/
│   └── skills/                # Habilidades especializadas del asistente de IA
│       ├── bot-flow-architect/
│       ├── order-status-tracker/
│       ├── whatsapp-engine/
│       └── verticals-playbook/
```
