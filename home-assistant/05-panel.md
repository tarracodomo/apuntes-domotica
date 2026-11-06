# El panel

El panel es lo que se usa a diario, así que conviene que sea claro y rápido.

## Estructura que funciona

- Una vista de resumen con el estado general: temperaturas, consumos, alarmas y puertas.
- Una vista por habitación, con las luces y los sensores de esa zona.
- Una vista de energía, con el consumo y el coste.
- Una vista de ajustes y diagnósticos, para no mezclarla con el uso diario.

## Tarjetas útiles

| Tarjeta | Para qué |
|---|---|
| Entidades | Lista compacta de estados |
| Botón | Encender o apagar con un toque |
| Medidor | Consumo, batería o humedad de un vistazo |
| Historia | Evolución de un sensor |
| Cámara | Vista en directo |
| Markdown | Notas y recordatorios |

## Mando desde el móvil

La aplicación oficial da notificaciones, localización y accesos directos. Con `notify.mobile_app_...` se pueden mandar avisos al teléfono con acciones, por ejemplo abrir la puerta o silenciar.

Para un panel fijo en la pared, una tablet vieja con la aplicación en modo panel y la pantalla siempre encendida es la solución más barata. Si quieres un panel pequeño dedicado, una pantalla táctil con ESP32 y LVGL hace el trabajo, aunque con menos flexibilidad.

## Energía

Con medidores en el cuadro se obtiene el consumo por franjas y el coste. Configura el precio de la luz con las horas valle y punta, y el panel de energía muestra el reparto. Es la tarjeta que más ayuda a bajar la factura.
