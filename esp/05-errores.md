# Errores que se repiten

## El módulo se reinicia en bucle

Casi siempre es alimentación. El cable USB fino no da los 500 mA que pide el módulo al conectar el WiFi. Prueba con otra fuente y con un condensador de 470 µF entre 3,3 V y masa, cerca de la placa.

## No conecta al WiFi

- Contraseña con caracteres raros o red de 5 GHz: el ESP8266 solo va a 2,4 GHz.
- El router tiene activado el aislamiento de clientes.
- La red oculta necesita configuración manual del SSID.

## El sensor da valores absurdos

- DHT leído demasiado a menudo.
- Cables largos sin apantallar hasta el sensor.
- Alimentación compartida con un relé que mete ruido.

## El ADC miente

El ADC del ESP8266 tiene un rango real limitado y no es lineal. En el ESP32, el ADC también se desvía sin calibrar y algunos pines no sirven para medir mientras el WiFi está activo. Para medidas serias, usa un sensor con salida digital o un chip externo.

## Sube el código pero no hace nada

- Pin equivocado: revisa la numeración real de la placa, no la del dibujo.
- La placa tiene el pin usado por el LED o por el arranque.
- El sensor necesita más tiempo de calentamiento del que le das.

## El registro se llena de avisos

Suele ser una plantilla que falla cuando un sensor no está disponible. Añade `float(0)` o un valor por defecto y desaparecen.
