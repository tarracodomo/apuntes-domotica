# Placas ESP

## Cuál elegir

| Placa | WiFi | Bluetooth | Notas |
|---|---|---|---|
| ESP8266 | Sí | No | Barata y suficiente para un sensor |
| ESP32 | Sí | Clásico y BLE | Doble núcleo, muchas entradas y ADC |
| ESP32-CAM | Sí | Sí | Cámara y ranura microSD, pocos pines libres |
| ESP32-C6 | WiFi 6 | BLE 5 | Thread y Zigbee, la más moderna |
| Wemos D1 | Sí | No | ESP8266 en formato Arduino UNO |
| Wemos D1 R32 | Sí | Sí | ESP32 en formato Arduino UNO |

## Cuándo basta un ESP8266

Para un DHT, un relé o un sensor de puerta, el ESP8266 sobra. Es más barato y consume menos en reposo. Su límite: un solo núcleo, menos memoria y solo un ADC.

## Cuándo hace falta un ESP32

- Cuando hay que leer varios sensores a la vez.
- Cuando se necesita Bluetooth.
- Cuando se quiere cámara o pantalla.
- Cuando se necesita dormir y despertar por un pin, que en el ESP8266 está más limitado.

## Avisos que se repiten

- Los pines del ESP32 no son todos iguales: algunos solo entran, otros no tienen ADC y otros están ocupados por el arranque. Consulta la tabla de pines antes de cablear.
- Alimenta los relés y los servos con una fuente aparte. El regulador de la placa no aguanta los picos.
- El ESP32-CAM necesita un adaptador USB-serie y poner GPIO0 a masa para cargar el código.
- Casi todas las placas trabajan a 3,3 V en sus pines. Un sensor de 5 V a la entrada puede dañarla.
