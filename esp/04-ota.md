# OTA: actualizar sin cable

Una vez que el módulo está en el techo o dentro de una caja, el cable ya no es una opción. OTA permite subir el firmware por la red.

## Requisitos

- El módulo debe estar conectado a la misma red que el equipo que compila.
- Tiene que estar compilado con OTA activado.
- Necesita contraseña de OTA; sin ella, cualquiera en la red podría subirle firmware.

En ESPHome, el bloque `ota:` con `password` es suficiente. El puerto por defecto es el 3232.

## Cuando falla

| Síntoma | Causa habitual |
|---|---|
| No aparece el dispositivo | Otra red o VLAN, o el nombre no resuelve |
| Se queda en Connecting | Contraseña de OTA distinta o firmware sin OTA |
| Se corta a medias | WiFi débil o el módulo entra en deep sleep |
| Vuelve al firmware anterior | Imagen corrupta; se reintenta por cable |

Lo primero en estos casos es probar por IP en lugar de por nombre. Si el módulo duerme, hay que despertarlo o dejarlo despierto para actualizarlo.

## Recuperación

Si el OTA ha dejado el módulo sin arrancar, casi siempre se recupera por cable USB. En el ESP8266 basta con mantener el pin de arranque a masa al conectar. En el ESP32-CAM, GPIO0 a masa.

Guarda el binario compilado de cada versión que funcione. Volver a una versión conocida es más rápido que depurar a oscuras.
