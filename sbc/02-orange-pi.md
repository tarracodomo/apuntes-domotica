# Orange Pi

## Qué la diferencia

Es más barata que la Raspberry Pi y algunas versiones llevan más puertos o más RAM por el mismo precio. A cambio, el soporte de software es menos pulido y hay que elegir bien la imagen.

## Sistema

Lo habitual es **Armbian**, que mantiene imágenes actualizadas para la mayoría de modelos. Algunos fabricantes publican su propia imagen oficial, a veces más completa en cuanto a drivers.

1. Descarga la imagen para tu modelo exacto. Un modelo equivocado no arranca.
2. Grábala en la tarjeta con balenaEtcher o con `dd`.
3. Arranca y entra con el usuario por defecto que indique la imagen. En Armbian suele pedir crear la contraseña de root en el primer arranque.
4. Ejecuta `armbian-config` para red, SSH, zona horaria y actualizaciones.

## Home Assistant

No hay imagen oficial de Home Assistant OS para Orange Pi. Las opciones reales son:

- **Docker con Home Assistant Container:** lo más estable y sin sorpresas. Se pierde la tienda de complementos.
- **Home Assistant Supervised:** da complementos, pero es una instalación no soportada oficialmente y se rompe con más facilidad tras actualizar.

Para un uso normal, Docker es la apuesta segura.

## Temperatura

```bash
cat /sys/class/thermal/thermal_zone0/temp
```

El valor viene en milésimas de grado: 45000 son 45 °C. Para un registro continuo:

```bash
watch -n 5 'awk "{printf \"%.1f C\n\", \$1/1000}" /sys/class/thermal/thermal_zone0/temp'
```

Estas placas se calientan más que una Raspberry y muchas vienen sin disipador. Con carga sostenida, un disipador y una caja ventilada son obligatorios.

## Alimentación

Es el punto débil de muchas versiones: el conector y la fuente. Usa la fuente recomendada por el fabricante. Con un cargador de móvil, los reinicios aleatorios y los fallos de USB son constantes.

## GPIO

Los pines no coinciden con los de Raspberry Pi, aunque el conector se parezca. Consulta el esquema de tu modelo antes de conectar nada: usar un sombrero de Raspberry tal cual puede dañar la placa.
