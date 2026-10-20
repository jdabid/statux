---
name: sdet-pipeline-mentor
description: >-
  Guía pedagógica, preparación de entrevistas técnicas y estándares de código para aspirantes a QA Automation Engineer (SDET) y Pipeline / Render TD. Integra pruebas automatizadas (Pytest, CI/CD, Docker) y automatización de procesos en el proyecto como portafolio profesional.
---

# SDET & Pipeline Developer Mentor Skill 🎯

Esta habilidad está diseñada para convertir este proyecto en un **portafolio de nivel profesional** y prepararte para conseguir tu primer empleo como:
1. **QA Automation Engineer / SDET (Software Development Engineer in Test)**
2. **Render TD / Pipeline Developer (VFX, Animación y Automatización)**

---

## 1. ¿Qué hacen estos roles? (Explicación para Estudiar)

### A. QA Automation Engineer (SDET)
* **En una frase:** Es un programador cuyo trabajo es crear robots de código que prueban otros programas las 24 horas del día para encontrar fallos antes de que los vea el cliente.
* **Analogía de la vida real:**  
  Imagina una fábrica de carros (como Toyota). En vez de contratar a una persona para que abra y cierre la puerta de un carro 50.000 veces a mano con cansancio, el SDET construye un brazo robótico que abre y cierra la puerta a toda velocidad y anota en una gráfica si la cerradura resistió.
* **Herramientas clave que debes dominar:** Python, `pytest`, Docker, GitHub Actions (CI/CD), Mocks, Postman/HTTPX para APIs y Selenium/Playwright para web.

### B. Render TD & Pipeline Developer
* **En una frase:** Es el ingeniero que construye los "caminos y tuberías" automatizadas para que los archivos (modelos 3D, renders, datos) viajen sin atascarse entre diferentes programas y computadoras.
* **Analogía de la vida real:**  
  Imagina un aeropuerto de carga. Los artistas 3D son los pasajeros con maletas gigantes. Si no hay bandas transportadoras automáticas, carritos de carga ni letreros, el aeropuerto colapsa. El **Pipeline Developer** construye las bandas transportadoras automáticas y se asegura de que ninguna maleta se pierda en el camino.
* **Herramientas clave que debes dominar:** Python avanzado, gestión de procesos en segundo plano, Docker, APIs REST, manejo de archivos/assets y scripts para granjas de renderizado o colas de trabajo.

---

## 2. El Vínculo Secreto: ¿Por qué eres el candidato perfecto?

Tanto el **SDET** como el **Pipeline Developer** comparten el mismo núcleo:
> **Desarrolladores Python expertos en automatización, colas de trabajo y control de calidad.**

En este proyecto (`empresa`), cada vez que construyamos una pieza, la construiremos con **mentalidad de SDET y Pipeline**:
1. **Pruebas Automatizadas con Pytest:** Cada endpoint de FastAPI tendrá su test automatizado que verifique que responde en menos de 50ms y con los datos correctos.
2. **Mocks y Simulación:** En vez de gastar dinero enviando mensajes reales de WhatsApp durante las pruebas, construiremos un "Mock" (un imitador falso) que verifique el envío sin costo.
3. **Pipeline con Docker y Redis:** El mismo concepto de encolar una orden para que el worker la procese en segundo plano es **idéntico a cómo una granja de renderizado encola una escena 3D para ser procesada por los servidores de render**.

---

## 3. Modo Preparación de Entrevistas (Cómo usar este skill)

Cuando quieras practicar para una entrevista laboral, solo debes pedirlo con comandos como:
- *"Hazme una pregunta típica de entrevista técnica para SDET Junior"*
- *"Explícame qué es una Fixture en Pytest con una analogía"*
- *"¿Cómo le explico este proyecto a un reclutador técnico en mi currículum (CV)?"*

---

## 4. 💡 Flashcard para Estudiar:
> **La diferencia entre QA Manual y SDET:**  
> - El QA Manual prueba haciendo clics con el ratón.  
> - El SDET programa código en Python que hace 1.000 pruebas por segundo de forma automática en un pipeline de integración continua (CI/CD).
