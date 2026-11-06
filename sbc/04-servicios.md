# Servicios propios con systemd

Para un script que debe arrancar solo y reiniciarse si falla, systemd es lo correcto.

## Ejemplo: lector de sensores

```bash
sudo nano /etc/systemd/system/lector.service
```

```ini
[Unit]
Description=Lector de sensores
After=network-online.target
Wants=network-online.target

[Service]
Type=simple
User=pi
WorkingDirectory=/home/pi/lector
ExecStart=/usr/bin/python3 /home/pi/lector/main.py
Restart=on-failure
RestartSec=10
StandardOutput=journal
StandardError=journal

[Install]
WantedBy=multi-user.target
```

Activar:

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now lector.service
sudo systemctl status lector.service
```

## Ver qué pasa

```bash
journalctl -u lector.service -f
journalctl -u lector.service -b --no-pager | tail -50
```

## Errores típicos

- Poner `ExecStart` con rutas relativas: usa siempre rutas absolutas.
- Ejecutar como root lo que no lo necesita.
- Olvidar `daemon-reload` después de editar el archivo.
- Un script que depende de la red sin `After=network-online.target`.

## Alternativa rápida

Para pruebas, `crontab -e` con `@reboot` cumple. Para producción, systemd: te da reinicio automático, registro y estado.
