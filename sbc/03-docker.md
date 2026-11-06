# Docker en placas SBC

## Instalación

```bash
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker $USER
```

Cierra sesión y vuelve a entrar para que el grupo se aplique. Comprueba con `docker run hello-world`.

## docker compose con Home Assistant y Mosquitto

```yaml
services:
  homeassistant:
    image: ghcr.io/home-assistant/home-assistant:stable
    container_name: homeassistant
    restart: unless-stopped
    privileged: true
    network_mode: host
    environment:
      - TZ=Europe/Madrid
    volumes:
      - ./homeassistant:/config
      - /etc/localtime:/etc/localtime:ro

  mosquitto:
    image: eclipse-mosquitto:2
    container_name: mosquitto
    restart: unless-stopped
    ports:
      - "1883:1883"
    volumes:
      - ./mosquitto/config:/mosquitto/config
      - ./mosquitto/data:/mosquitto/data
```

Se arranca con `docker compose up -d` y se ve el estado con `docker compose ps`.

## Cosas que se aprenden a golpes

- **`network_mode: host` con HA:** necesario para descubrir dispositivos por mDNS. Si no, no ve los ESPHome.
- **Permisos:** las carpetas montadas deben pertenecer al usuario correcto. Un `chown` mal hecho deja a Home Assistant sin poder escribir.
- **Registros:** `docker compose logs -f --tail 100` es el primer sitio donde mirar cuando algo no arranca.
- **Actualizar:** `docker compose pull && docker compose up -d`. Lee las notas antes.
- **Disco:** las imágenes ocupan varios gigas. `docker system prune` de vez en cuando, con cuidado de no borrar lo que se usa.

## Copias

Todo lo importante está en las carpetas montadas. Copiar el directorio del proyecto con `rsync` equivale a copiar el sistema entero, siempre que los contenedores estén parados o la base de datos se copie de forma consistente.
