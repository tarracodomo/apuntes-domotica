# ESPHome: estación meteorológica

ESPHome se queda con el módulo, se conecta a la red y aparece en Home Assistant. El archivo de configuración es todo el programa.

## Configuración completa

```yaml
esphome:
  name: meteo-salon
  friendly_name: Meteo salón

esp8266:
  board: nodemcuv2

logger:

api:
  encryption:
    key: "pega_aqui_la_clave"

ota:
  - platform: esphome
    password: "una_clave_larga"

wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password
  ap:
    ssid: "Meteo Fallback"

captive_portal:

sensor:
  - platform: dht
    pin: D4
    model: DHT22
    temperature:
      name: "Temperatura salón"
    humidity:
      name: "Humedad salón"
    update_interval: 60s

text_sensor:
  - platform: wifi_info
    ip_address:
      name: "IP"
```

## Puntos que importan

- **Secretos:** las credenciales del WiFi van en `secrets.yaml`, que no se sube al repositorio.
- **Clave de API:** sin ella, cualquiera en la red puede leer el dispositivo. Con ESPHome moderno se genera sola.
- **Intervalo:** leer un DHT cada 60 segundos es correcto. Si se lee cada segundo, el sensor da errores.
- **Fallback:** la red de reserva permite recuperar el módulo si cambias la contraseña del WiFi.

## Añadir un relé

```yaml
switch:
  - platform: gpio
    pin: D1
    name: "Luz terraza"
    restore_mode: ALWAYS_OFF
```

`restore_mode: ALWAYS_OFF` evita que al reiniciar se encienda sola, que es un susto habitual.

## Compilar y subir

La primera vez por cable USB, después por OTA. ESPHome compila en el equipo donde corre; si va lento, compila desde la interfaz web en un equipo con más memoria.
