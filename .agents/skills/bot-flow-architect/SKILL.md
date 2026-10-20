---
name: bot-flow-architect
description: >-
  Diseña y valida flujos conversacionales de bots, árboles de decisión, plantillas interactivas de WhatsApp y lógica de interacción para clientes de negocios locales (restaurantes, talleres, barberías, supermercados).
---

# Bot Flow Architect Skill

Esta habilidad proporciona las directrices y patrones para diseñar flujos de conversación en WhatsApp y chatbots para negocios locales, maximizando la tasa de conversión y minimizando la fricción.

## 1. Principios de Conversación
1. **Regla de los 3 Clics:** El usuario debe poder completar su consulta o pedido en máximo 3 interacciones o toques.
2. **Uso de Botones y Listas:** Siempre que sea posible, utilizar botones interactivos de WhatsApp (`quick_reply`, `list_picker`) en lugar de pedir que el cliente escriba texto libre para opciones cerradas.
3. **Manejo de Fallbacks Inteligente:** Si el usuario escribe algo que el bot no comprende, ofrecer un menú claro de opciones o transferir la conversación a un operador humano.

## 2. Estructura de un Flujo Conversacional
Cada flujo debe documentarse con:
- **Disparador (Trigger):** Código QR físico, palabra clave ("menu", "pedido", "turno"), o webhook de cambio de estado.
- **Contexto y Memoria:** Datos que se guardan durante la sesión (nombre, teléfono, ID de pedido, dirección).
- **Acciones:** Notificación enviada, actualización de base de datos o llamada a API externa.
- **Salida:** Confirmación visual y enlace de seguimiento en vivo.

## 3. Ejemplo de Estructura de Mensaje de Estado

```text
🛎️ *¡Actualización de tu pedido en {nombre_negocio}!*
---------------------------------------
Hola *{nombre_cliente}*, tu orden *#{numero_orden}* acaba de pasar a:

🔥 *ESTADO:* {nombre_estado}
_{descripcion_estado}_

⏳ *Tiempo estimado restante:* {tiempo_estimado} min

👉 Sigue tu orden en tiempo real aquí:
https://tu-plataforma.com/track/{tracking_token}
```
