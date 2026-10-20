---
name: whatsapp-engine
description: >-
  Guía la configuración, integración, envío de plantillas y procesamiento de webhooks con la API de WhatsApp (Meta Cloud API, proveedores BSP o librerías de conexión).
---

# WhatsApp Engine Skill

Esta habilidad contiene las instrucciones y mejores prácticas técnicas para integrar WhatsApp como el canal de notificación e interacción principal.

## 1. Opciones de Conexión

1. **Meta WhatsApp Cloud API (Oficial - Recomendado para producción):**
   - Requiere cuenta de Meta Business Manager y verificación.
   - Permite enviar plantillas oficiales aprobadas para iniciar conversaciones.
   - Máxima estabilidad y cero riesgo de baneo de número.
2. **Gateway / Proveedores BSP (Twilio, Gupshup, Weni, 360dialog):**
   - Ideal para agilizar la integración con SDKs listos.
3. **Simulador Local (Para Desarrollo y Demos):**
   - Durante el desarrollo y pruebas locales, se recomienda utilizar un mock/simulador interactivo en pantalla que emula la conversación de WhatsApp en tiempo real para no gastar saldo de API ni requerir credenciales inmediatas.

## 2. Tipos de Mensajes Clave

- **Mensajes de Plantilla (Template Messages):** Necesarios para notificaciones proactivas cuando la ventana de 24 horas del cliente está cerrada.
- **Mensajes Interactivos (Interactive Messages):**
  - `button`: Para confirmar citas o aprobar presupuestos (ej. `[Aprobar Reparación]`, `[Rechazar]`).
  - `list`: Para selección de opciones como servicios o barberos disponibles.

## 3. Manejo de Webhooks
- El endpoint `/api/webhooks/whatsapp` debe responder con HTTP `200 OK` inmediatamente para evitar reintentos por parte de Meta.
- Enviar el procesamiento del mensaje recibido a una cola en segundo plano (Background Worker / Queue).
