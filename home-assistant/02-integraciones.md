# Integraciones que uso

## MQTT con Mosquitto

Es el transporte de casi todo lo que no es ESPHome: sensores baratos, Zigbee, Tasmota.

```yaml
mqtt:
  broker: 192.168.1.50
  port: 1883
  username: homeassistant
  password: !secret mqtt_password
```

El broker va aparte, en Docker o como complemento. Usa usuario y contraseña; nunca lo dejes abierto.

## ESPHome

Cada módulo aparece solo en Home Assistant, sin configurar nada a mano. Basta con que el YAML del dispositivo tenga `api:` y estén en la misma red.

Si no aparece, revisa que el módulo resuelva por mDNS. En redes con VLAN separadas hay que indicar la IP del servidor en la configuración.

## Telegram

1. En Telegram, habla con `@BotFather` y crea un bot con `/newbot`. Guarda el token.
2. En Home Assistant, Ajustes > Dispositivos y servicios > Añadir integración > Telegram.
3. Pega el token. El bot te dará un código para autorizar tu chat.
4. Añade tu `chat_id` numérico a la lista de permitidos.

Para enviar un aviso desde una automatización:

```yaml
action:
  - service: notify.telegram
    data:
      message: "La puerta del garaje lleva 10 minutos abierta"
```

## HACS

Instala integraciones y tarjetas que no están en el catálogo oficial. Se instala una vez y luego se actualiza desde la interfaz. Ten en cuenta que el soporte corre por cuenta de cada autor.

## Cámaras

- **RTSP directo:** vale para casi cualquier cámara IP y es lo más ligero.
- **Frigate:** detección de personas y objetos con grabación en disco. Pide bastante CPU; en Raspberry Pi solo funciona bien con un acelerador Coral o con una GPU.

## Bluetooth

El Bluetooth del propio servidor suele tener poco alcance. Un ESP32 con Bluetooth Proxy en el pasillo amplía la cobertura de los sensores de puerta y de los termómetros baratos.
