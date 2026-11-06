# Instalación de Home Assistant

Hay tres formas de instalarlo y la elección depende de la placa y de lo que quieras hacer después.

| Forma | Qué es | Cuándo usarla |
|---|---|---|
| HAOS | Sistema completo, con supervisores y complementos | Raspberry Pi o PC, es la opción recomendada |
| Home Assistant Container | Solo el núcleo, en Docker | Orange Pi, NAS o servidor con Docker |
| Home Assistant Core | Instalación en Python | Pruebas y desarrollo |

## Raspberry Pi con HAOS

1. Descarga la imagen de Home Assistant OS desde la web oficial.
2. Grábala con Raspberry Pi Imager o con balenaEtcher en la tarjeta microSD.
3. Mete la tarjeta, conecta el cable de red y la alimentación.
4. Espera entre 10 y 20 minutos: la primera puesta en marcha instala y amplía la partición.
5. Abre `http://homeassistant.local:8123` o la IP que tenga la placa.

Si no responde, mira en el router qué IP ha tomado. Conviene reservarla desde el router para que no cambie.

Recomendaciones: Raspberry Pi 4 con 2 GB va bien; con Frigate o muchas cámaras, mejor 4 GB o 8 GB y un SSD por USB en lugar de la tarjeta SD. La SD se degrada con las escrituras continuas de la base de datos.

## Orange Pi o cualquier Linux con Docker

Home Assistant OS no tiene imagen oficial para Orange Pi. La vía práctica es Armbian y Docker:

```bash
docker run -d \
  --name homeassistant \
  --privileged \
  --restart=unless-stopped \
  -e TZ=Europe/Madrid \
  -v /opt/homeassistant:/config \
  --network=host \
  ghcr.io/home-assistant/home-assistant:stable
```

La carpeta `/config` es todo el sistema: ahí viven `configuration.yaml`, la base de datos y las copias. Guárdala con permisos de root y haz copia aparte.

Con `--network=host` la web queda en el puerto 8123 y el descubrimiento de dispositivos funciona sin abrir puertos uno a uno.

## Primer arranque

- Crea el usuario y pon una contraseña larga.
- En Ajustes, revisa la zona horaria y la moneda.
- Instala la integración de tu router o de la red para tener presencia, si la necesitas.
- Antes de tocar nada, programa copias automáticas.

## Actualizaciones

En HAOS se actualiza desde Ajustes, con el botón de actualizar. En Docker:

```bash
docker pull ghcr.io/home-assistant/home-assistant:stable
docker restart homeassistant
```

Lee las notas de la versión antes de saltar de versión mayor: los cambios en integraciones rompen automatizaciones más a menudo de lo que parece.
