# Hardware para Meshtastic

Todos los equipos llevan un microcontrolador y un radio LoRa. La diferencia está en la pantalla, el GPS, la batería y el consumo.

| Equipo | Microcontrolador | Lo que aporta |
|---|---|---|
| Heltec WiFi LoRa 32 V3 | ESP32-S3 + SX1262 | Pantalla OLED, WiFi y Bluetooth. La más económica para el primer nodo |
| LILYGO T-Beam | ESP32 + SX1262/SX1276 | GPS y soporte de célula 18650. Para llevar encima o en el coche |
| RAK WisBlock | nRF52 o ESP32, modular | Piezas que se encajan. Bajo consumo y mucha flexibilidad |
| T-Deck | ESP32-S3 | Teclado y pantalla grande. Mensajería sin teléfono |
| Seeed XIAO ESP32S3 + Wio-SX1262 | ESP32-S3 | Muy pequeña, para nodos escondidos o proyectos propios |

## Cuál elegir según el uso

- **Primer nodo para trastear:** Heltec V3. Barata, con pantalla y bien documentada.
- **Nodo portátil con GPS:** T-Beam. La célula 18650 se cambia en segundos.
- **Nodo fijo en el monte con placa solar:** RAK o Heltec en caja estanca. El consumo importa más que la pantalla.
- **Sin teléfono a mano:** T-Deck.

## La banda, primero

En Europa hay que comprar la versión de **868 MHz**. La de 915 MHz es para América y no se comunica con la europea, aunque el equipo sea idéntico por fuera. Comprueba la banda antes de pagar: es el error más caro y más frecuente.

## Antenas

- La antena tiene que ser de la banda del equipo.
- Una antena de 915 MHz en un equipo de 868 reduce el alcance y puede dañar la etapa de radio.
- **Nunca enciendas el equipo sin antena conectada.** Es la forma más rápida de quemar el módulo.
- Las antenas de goma que vienen de serie sirven para empezar. Una exterior en el tejado cambia el resultado por completo.
- El conector suele ser SMA o IPEX. Comprueba cuál es: no son compatibles.

## Alimentación y autonomía

- Un nodo con una 18650 de buena calidad aguanta días o semanas, según el tráfico.
- El GPS es lo que más gasta: si no lo necesitas, desactívalo o baja la frecuencia de posición.
- La pantalla también consume; muchos equipos permiten apagarla o bajar el brillo.
- Para exterior: panel solar de 5 a 10 W, regulador y batería. Con eso, un nodo fijo puede quedarse meses sin mantenimiento.

## Caja y montaje

- Caja estanca con prensaestopas para el cable de la antena.
- La antena fuera y lo más alta posible; el mástil de una antena de TV es un buen sitio.
- Evita el metal alrededor de la antena, incluida la propia caja si es metálica.
- Si el nodo va en interior, colócalo en la ventana que mire hacia el resto de la red.

## Antes de instalarlo

Configura el equipo en casa, con la región y el canal correctos, y comprueba que ve otros nodos. Subir a un tejado para descubrir que la región estaba mal es la manera más común de perder una tarde.
