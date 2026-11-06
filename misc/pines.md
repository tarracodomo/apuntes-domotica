# Pines

## ESP32

| Pin | Aviso |
|---|---|
| GPIO 0 | Estado de arranque. A masa para cargar firmware |
| GPIO 2 | LED de la placa en muchas versiones |
| GPIO 6 a 11 | Conectados a la memoria flash, no se usan |
| GPIO 34 a 39 | Solo entrada, sin resistencia interna |
| GPIO 12, 15 | Condicionan el arranque según su nivel |
| GPIO 21, 22 | I2C por defecto |
| GPIO 16, 17 | UART2, libres para periféricos |

## ESP8266

| Pin | Uso |
|---|---|
| D0 | GPIO16, solo despierta del deep sleep con cable a RST |
| D1, D2 | I2C habitual |
| D3, D4 | Buenos para sensores y relés, con cuidado en el arranque |
| A0 | Única entrada analógica, máximo 1 V |
| TX, RX | Serie, ocupados por el USB |

## Raspberry Pi

| Pin físico | Función |
|---|---|
| 1 | 3,3 V |
| 2 y 4 | 5 V |
| 6, 9, 14, 20, 25, 30, 34, 39 | Masa |
| 3 | SDA (I2C) |
| 5 | SCL (I2C) |
| 8, 10 | UART |
| 11, 12, 13, 15, 16, 18, 22 | GPIO y PWM |

Los pines de la Raspberry son de 3,3 V y no toleran 5 V. Un sensor de 5 V necesita adaptador de nivel o divisor de tensión, igual que con los ESP.

## Regla general

Antes de conectar, comprueba tres cosas: la tensión que entrega el sensor, la que admite el pin y si el pin está libre en el arranque. Casi todos los módulos muertos han caído por una de esas tres.
