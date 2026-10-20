---
name: git-commit-standards
description: >-
  Estandariza los mensajes de confirmación de Git (Conventional Commits), plantillas de commits, nombres de ramas y flujo de trabajo en Git para mantener un historial profesional y listo para entrevistas de SDET / Pipeline Developer.
---

# Git Commit Standards Skill (Nomenclatura y Plantillas de Git) 🌿

Esta habilidad estandariza la forma en que guardamos los cambios en Git usando el estándar de la industria: **Conventional Commits**.

---

## 1. ¿Qué es un estándar de Git? (Explicación para Estudiar)

* **¿Qué es en una sola frase?:** Es una regla universal para ponerle títulos claros a los cambios en el código, de modo que cualquier programador sepa qué se hizo sin tener que leer miles de líneas.
* **La analogía del diario de a bordo de un avión:**  
  Imagina la bitácora de mantenimiento de un avión de pasajeros. Si el mecánico escribe: *"le moví una cosa"*, *"cambios de hoy"* o *"probando a ver si vuela"*, nadie querría subirse a ese avión. El mecánico escribe con precisión: `Reparación(Frenos): cambiar pastillas desgastadas del ala derecha`. En programación profesional, Git es la bitácora de tu avión.
* **¿Qué problema resuelve?:** Elimina los mensajes vagos como *"subiendo cambios"*, *"arreglos"*, *"ahora sí funciona"*, que causan pésima impresión en reclutadores y hacen imposible encontrar dónde se rompió algo.

---

## 2. La Fórmula de Oro de un Commit Profesional

Cada commit sigue esta estructura exacta:

```text
<tipo>(<alcance>): <descripción corta en minúsculas y sin punto final>
```

Ejemplos reales para nuestro proyecto:
- `feat(orders): crear comando para pasar pedido a estado en_horno`
- `test(orders): agregar pruebas unitarias con pytest para cambio de estado`
- `ci(docker): agregar servicio de redis y postgres en docker-compose`
- `docs(readme): agregar mision y submarcas de statux`

---

## 3. El Diccionario de Tipos (Conventional Commits)

| Prefijo | ¿Cuándo se usa? | Ejemplo en STATUX |
| :--- | :--- | :--- |
| **`feat:`** | Nueva función que ve el usuario o la API. | `feat(whatsapp): enviar notificacion cuando orden pasa a lista` |
| **`fix:`** | Arreglo de un error o falla (*bug*). | `fix(orders): corregir calculo de tiempo restante de entrega` |
| **`test:`** | Agregar o mejorar pruebas (*Crucial para SDET*). | `test(kds): validar que los botones de cocina cambien el color` |
| **`ci:`** | Docker, pipelines, GitHub Actions (*Crucial para Pipeline TD*). | `ci(docker): configurar healthcheck para base de datos postgres` |
| **`refactor:`** | Mejorar código interno sin cambiar lo que hace. | `refactor(database): simplificar sesion async de sqlalchemy` |
| **`docs:`** | Cambios en documentación o comentarios. | `docs(sprint): actualizar tareas completadas del sprint 1` |
| **`chore:`** | Tareas rutinarias, dependencias o configuración. | `chore(deps): agregar pydantic y uvicorn a requirements.txt` |

---

## 4. Convención de Nombres de Ramas (Branches)

Cuando creemos ramas separadas para trabajar en equipo o en features aisladas:

- `feature/nombre-de-la-tarea` (ej. `feature/kds-screen`)
- `test/nombre-del-modulo` (ej. `test/orders-cqrs`)
- `hotfix/descripcion-del-bug` (ej. `hotfix/webhook-timeout`)

---

## 5. 💡 Flashcard para Estudiar (Para tu entrevista SDET / Pipeline):
> **¿Por qué los reclutadores revisan tu historial de Git?**  
> Porque un historial con mensajes como `feat:`, `test:` y `ci:` demuestra de inmediato que **sabes trabajar en equipo, respetas los estándares internacionales y tienes disciplina de ingeniería**.
