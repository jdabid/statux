---
name: sprint-manager
description: >-
  Gestiona la metodología de trabajo por Sprints, define tareas atómicas y mantiene actualizado en tiempo real el archivo SPRINT.md conforme se avanza en el proyecto.
---

# Sprint Manager Skill (Gestión Ágil y Progreso Paso a Paso)

Esta habilidad asegura que el desarrollo del proyecto avance de forma ordenada en bloques de trabajo enfocados (Sprints) y que el documento `SPRINT.md` refleje fielmente el estado real de cada tarea.

---

## 1. ¿Qué es un Sprint? (Explicación para Estudiar)

- **En una frase:** Un Sprint es un bloque corto de trabajo donde nos enfocamos en una sola meta concreta, sin distraernos con el resto del proyecto.
- **Analogía de la vida real:**  
  Imagina que vas a construir una casa. No puedes poner el techo, pintar las paredes y colocar las cortinas todo al mismo tiempo.  
  - **Sprint 1:** Poner los cimientos y el suelo firme.  
  - **Sprint 2:** Levantar las paredes de la cocina.  
  - **Sprint 3:** Poner el techo y las puertas.  
  Cada Sprint deja algo terminado y usable.
- **¿Qué problema resuelve?:** Evita la parálisis por exceso de ideas y el desorden de empezar 10 cosas a la vez y no terminar ninguna.

---

## 2. Convención de Estados de Tareas en `SPRINT.md`

Toda tarea debe usar una de estas marcas en su casilla de verificación:

- `[ ]` **Pendiente:** La tarea está definida pero aún no se ha iniciado.
- `[⏳]` **En Progreso:** El asistente o usuario está trabajando en ella activamente en este turno.
- `[x]` **Completada:** La tarea fue construida, verificada y está funcionando.

---

## 3. Regla de Oro de Actualización Automática

1. **Antes de empezar una tarea:** Marcarla como `[⏳] En Progreso` en `SPRINT.md`.
2. **Al terminar y verificar la tarea:** Marcarla como `[x]` e incrementar el porcentaje de la barra de progreso del Sprint.
3. **Cero tareas huérfanas:** Cada archivo de código nuevo debe responder directamente a una tarea del Sprint actual.
