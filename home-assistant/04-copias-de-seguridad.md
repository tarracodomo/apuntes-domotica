# Copias de seguridad

Una instalación sin copia es una instalación que se va a perder. La tarjeta SD falla, el SSD se corrompe y una actualización puede dejar el sistema a medias.

## Qué hay que copiar

- **Copia completa:** todo, incluida la base de datos. Es la que se restaura en un equipo nuevo.
- **Copia parcial:** solo la configuración, sin historial. Pesa mucho menos y sirve para llevar los ajustes a otra instalación.

## Cómo se hacen

Ajustes > Sistema > Copias de seguridad. Ahí se descarga un archivo comprimido, se restaura o se programa la copia automática.

Programa una copia automática diaria o semanal y activa que se borren las antiguas. Sin límite, el disco se llena y el sistema empieza a fallar.

## Sacarlas del equipo

Lo importante: una copia en el mismo disco que el sistema no es una copia. Opciones:

1. Descargar el archivo a mano de vez en cuando.
2. Montar un recurso de red y guardarlas ahí.
3. Copiar la carpeta de copias con `rsync` a un NAS o a otro equipo:

```bash
rsync -av --delete /opt/homeassistant/backups/ usuario@nas:/volume1/backup/ha/
```

Y si es posible, una copia en otro sitio físico. Un incendio o un robo se lleva las dos si están en la misma casa.

## Restaurar

En una instalación nueva, en la pantalla de bienvenida hay un enlace para restaurar desde una copia. En una que ya funciona: Ajustes > Sistema > Copias de seguridad > Restaurar. Reinicia al terminar.

Después de restaurar, revisa las IP de los dispositivos: si la copia viene de otra red, las integraciones que apuntan a direcciones fijas hay que corregirlas.
