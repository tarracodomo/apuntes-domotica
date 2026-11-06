# Raspberry Pi

## Puesta en marcha

1. Graba la imagen con Raspberry Pi Imager. En las opciones avanzadas puedes definir usuario, contraseña, WiFi y activar SSH antes de arrancar.
2. Arranca y espera. El primer arranque amplía la partición y tarda un rato.
3. Entra por SSH:

```bash
ssh usuario@raspberrypi.local
```

## Ajustes básicos

```bash
sudo raspi-config
```

Desde ahí se cambia la contraseña, la zona horaria, el nombre del equipo y se activan las interfaces.

```bash
sudo apt update && sudo apt full-upgrade -y
sudo apt install -y htop curl git
```

## IP fija

Mejor reservarla en el router que fijarla a mano. Si no hay acceso al router, con NetworkManager:

```bash
sudo nmcli con mod "preconfigured" ipv4.addresses 192.168.1.60/24
sudo nmcli con mod "preconfigured" ipv4.gateway 192.168.1.1
sudo nmcli con mod "preconfigured" ipv4.dns 192.168.1.1
sudo nmcli con mod "preconfigured" ipv4.method manual
sudo nmcli con up "preconfigured"
```

## Temperatura y salud

```bash
vcgencmd measure_temp
vcgencmd get_throttled      # 0x0 significa que no ha habido problemas
df -h                       # espacio en disco
free -h                     # memoria
```

Si `get_throttled` no da cero, la placa ha sufrido caídas de tensión o sobrecalentamiento. Cambia la fuente: la mayoría de los fallos raros vienen de ahí.

## Tarjeta SD o SSD

La SD se degrada con escrituras continuas. Para Home Assistant, bases de datos o registro constante, un SSD por USB es mucho más fiable. En la Pi 5 hace falta además un adaptador compatible y, según el caso, alimentación extra.

## Copias

```bash
rsync -av --delete /home/usuario/datos/ usuario@nas:/backup/pi/
```

Una copia automática con `cron` a un NAS resuelve el problema sin pensar en ello.
