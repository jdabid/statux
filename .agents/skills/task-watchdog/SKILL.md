---
name: task-watchdog
description: >-
  Supervisa tareas, comandos y ejecuciones; si una tarea tarda 63 segundos o más en dar respuesta, activa un protocolo de diagnóstico de causa raíz (RCA) y genera un informe claro con la solución más eficiente.
---

# Task Watchdog Skill (Monitor de Tiempo y Diagnóstico de 63 Segundos) ⏱️

Esta habilidad establece el protocolo de supervisión para detectar tareas lentas, bloqueos o comandos que superen los 63 segundos, generando un informe de diagnóstico inmediato para resolver el problema sin perder tiempo.

---

## 1. ¿Qué es un Watchdog? (Explicación para Estudiar)

* **En una frase:** Es un "perro guardián digital" con un cronómetro en la mano que ladra si algo se queda congelado o tarda más de lo debido.
* **Analogía de la vida real:**  
  Imagina que pides una pizza en un restaurante express. El mesero tiene un cronómetro. Si a los 63 segundos el horno no ha sacado la masa, el supervisor va de inmediato a la cocina a mirar si el gas se apagó o si faltó leña, antes de que el cliente se desespere.
* **¿Qué problema resuelve?:** Evita la incertidumbre de quedarse mirando una pantalla en blanco o una terminal congelada sin saber si el programa está trabajando o si murió silenciosamente.

---

## 2. El Protocolo de Alerta de 63 Segundos

Cada vez que un proceso, comando de terminal (`docker build`, `pip install`, `pytest`, etc.) o tarea de background tarde **63 segundos** sin responder, se debe emitir este informe estructurado:

```markdown
⏱️ **ALERTA DE TIEMPO (Umbral de 63 Segundos Superado)**
-----------------------------------------------------------------
📍 **¿Qué se estaba ejecutando?**
[Nombre de la tarea, comando o endpoint exacto]

🔍 **¿Dónde se produjo la pausa/espera?**
[Explicación en palabras sencillas: ej. esperando descarga de red, base de datos bloqueada, dependencia pesada compilando]

🧠 **Causa Raíz (¿Por qué pasó?):**
[Explicación didáctica del motivo técnico detrás de la lentitud]

🛠️ **Solución más Eficiente y Efectiva (Plan de Acción):**
1. [Paso inmediato para destrabar o acelerar el proceso]
2. [Ajuste preventivo para que no vuelva a ocurrir]
-----------------------------------------------------------------
```

---

## 3. Conexión con tu perfil SDET & Pipeline Developer

En la industria del software y la animación:
- En **QA Automation (SDET):** Un test colgado que tarda minutos bloquea el pipeline de despliegue de toda la empresa (*CI/CD bottleneck*). Saber diagnosticar timeouts es una de las preguntas fijas en entrevistas técnicas.
- En **Render TD & Pipeline:** Si un render o exportación de archivo 3D se traba en la granja de servidores (*hung render job*), cuesta cientos de dólares por hora. Los Pipeline Developers crean *watchdogs* automáticos para cancelar y reintentar la tarea.

---

## 4. 💡 Flashcard para Estudiar:
> **Timeout vs. Deadlock:**  
> - **Timeout:** El tiempo límite de espera que permitimos antes de cancelar algo (en nuestro caso, 63 segundos).  
> - **Deadlock (Bloqueo mutuo):** Cuando dos procesos se quedan esperando el uno al otro eternamente y ninguno avanza si el Watchdog no interviene.
