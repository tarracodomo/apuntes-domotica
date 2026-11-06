# Deep sleep: meses con una batería

Un módulo despierto todo el día consume decenas de miliamperios. Dormido, unas decenas de microamperios. La diferencia es pasar de días a meses con la misma pila.

## En ESPHome

```yaml
deep_sleep:
  run_duration: 20s
  sleep_duration: 15min
```

El módulo despierta, mide, publica y vuelve a dormir. En Home Assistant el sensor aparece como no disponible mientras duerme, algo normal.

## Despertar por un pin

```yaml
binary_sensor:
  - platform: gpio
    pin:
      number: GPIO4
      mode: INPUT_PULLUP
    name: "Puerta"

deep_sleep:
  wakeup_pin: GPIO4
  wakeup_pin_mode: KEEP_AWAKE
```

Así el sensor de puerta duerme y solo despierta cuando alguien la abre.

## Cuentas de consumo

Una lectura cada 15 minutos son 96 al día. Con un módulo que consume 20 mA durante 20 segundos y 50 µA el resto del tiempo, la media sale en torno a 0,4 mA. Con una pila de 2500 mAh, eso son varios meses de autonomía.

Los números reales dependen de la placa, del regulador y de si hay un LED encendido. Muchas placas llevan un LED de encendido que se come toda la autonomía: hay que cortarlo.

## Avisos

- En el ESP8266 solo el pin RST despierta y hay que cablearlo.
- El ESP32 despierta por sensores de contacto, pero no todos los pines valen.
- Si el módulo no se conecta al WiFi en el tiempo de actividad, se pierde la lectura. Deja margen: 15 o 20 segundos es razonable.
- Con batería, usa una fuente con regulador de bajo consumo. Un convertidor barato puede gastar más que la propia placa.
