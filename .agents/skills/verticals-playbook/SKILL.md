---
name: verticals-playbook
description: >-
  Manual de especificaciones y modelos de datos por industria: Restaurantes, Supermercados, Barberías y Talleres Mecánicos. Contiene flujos, estados predefinidos y copys de WhatsApp.
---

# Verticals Playbook Skill

Este manual define las reglas de negocio, esquemas de datos y mensajes específicos para cada una de las 4 industrias objetivo.

---

## 1. 🍕 Vertical: Restaurantes (GastroBot / FoodFlow)

### Estados del Pedido:
1. `RECEIVED` - Pedido Recibido y Confirmado.
2. `PREPARING` - En Preparación en Cocina.
3. `IN_OVEN` - En el Horno / Plancha (clave para pizzerías y asaderos).
4. `READY_TO_SERVE` - Listo para Servir en Mesa / Listo para Recoger en Barra.
5. `OUT_FOR_DELIVERY` - En Camino con el Domiciliario (si aplica).
6. `DELIVERED` - Consumido / Entregado.

### Datos Específicos:
- `tipo_entrega`: `MESA`, `PARA_LLEVAR`, `DOMICILIO`.
- `numero_mesa`: string / int opcional.
- `items`: Lista de platos con notas/modificadores ("sin cebolla").

---

## 2. 🚗 Vertical: Taller Mecánico (AutoFlow)

### Estados del Servicio:
1. `CHECKIN` - Vehículo recibido (con registro fotográfico inicial).
2. `DIAGNOSING` - En inspección y diagnóstico técnico.
3. `QUOTATION_PENDING` - Esperando aprobación de presupuesto y repuestos por WhatsApp.
4. `IN_REPAIR` - En proceso de reparación / cambio de piezas.
5. `ROAD_TEST` - En prueba de ruta y control de calidad.
6. `READY_FOR_PICKUP` - Vehículo listo para entrega y pago.

### Acción Crítica en WhatsApp:
Envío de botón interactivo: `[✅ Aprobar Presupuesto: $120.000]` o `[📞 Hablar con el Mecánico]`.

---

## 3. ✂️ Vertical: Barbería / Salón (BarberFlow)

### Estados del Turno:
1. `BOOKED` - Cita agendada.
2. `REMINDER_SENT` - Recordatorio automático enviado 2 horas antes.
3. `NEXT_IN_LINE` - "Tu barbero está terminando, eres el siguiente en 10 min".
4. `IN_CHAIR` - En atención.
5. `COMPLETED` - Servicio finalizado (dispara encuesta de 1 a 5 estrellas y re-agendamiento automático en 20 días).

---

## 4. 🛒 Vertical: Supermercado / Tienda de Conveniencia (MarketFlow)

### Estados de la Compra:
1. `ORDER_PLACED` - Lista de mercado recibida.
2. `PICKING` - Operario alistando los productos en góndola.
3. `PACKED` - Empacado y pesado.
4. `READY_OR_SHIPPED` - Listo en caja para recoger o en ruta de reparto.
