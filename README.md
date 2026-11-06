# Apuntes de domótica

Notas de trabajo sobre domótica: Home Assistant, módulos ESP, Raspberry Pi y Orange Pi. Cada guía está escrita desde la práctica, con los comandos y las conexiones tal como los uso, y con los errores que me he ido encontrando.

| Bloque | Qué encontrarás |
|---|---|
| [Home Assistant](home-assistant/) | Instalación, integraciones, automatizaciones, copias y panel |
| [ESP y ESPHome](esp/) | Placas, configuración, ahorro de batería, OTA y errores |
| [Placas SBC](sbc/) | Raspberry Pi, Orange Pi, Docker y servicios |
| [Meshtastic](meshtastic/) | Radio LoRa en malla: qué es, hardware y errores |
| [Varios](misc/) | Tabla de pines y glosario |

## Home Assistant

- [Instalación](home-assistant/01-instalacion.md): HAOS en Raspberry Pi y Docker en Orange Pi.
- [Integraciones](home-assistant/02-integraciones.md): MQTT, ESPHome, Telegram, HACS.
- [Automatizaciones](home-assistant/03-automatizaciones.md): YAML y ejemplos reales.
- [Copias de seguridad](home-assistant/04-copias-de-seguridad.md): qué copiar y dónde guardarlo.
- [Panel](home-assistant/05-panel.md): paneles y tarjetas útiles.

## ESP

- [Placas](esp/01-placas.md): ESP32, ESP8266, ESP32-CAM y ESP32-C6.
- [ESPHome](esp/02-esphome.md): estación meteorológica completa.
- [Deep sleep](esp/03-deep-sleep.md): meses de batería.
- [OTA](esp/04-ota.md): actualizar sin cable.
- [Errores](esp/05-errores.md): los fallos que más se repiten.

## Placas SBC

- [Raspberry Pi](sbc/01-raspberry-pi.md)
- [Orange Pi](sbc/02-orange-pi.md)
- [Docker](sbc/03-docker.md)
- [Servicios con systemd](sbc/04-servicios.md)

## Meshtastic

- [Qué es y cómo funciona](meshtastic/01-que-es.md): LoRa, la malla, canales y claves, y sus límites.
- [Hardware](meshtastic/02-hardware.md): Heltec, T-Beam, RAK, T-Deck, antenas y autonomía.
- [En España y errores](meshtastic/03-espana-y-errores.md): banda de 868 MHz, región y tabla de fallos.

## Aviso

Los datos son orientativos. Comprueba siempre la documentación del fabricante de tu placa, porque cambia entre revisiones.

---

Proyecto relacionado: [Tarraco Domo](https://github.com/icemancoin/tarracodomo-web), domótica y monitorización en Tarragona.
