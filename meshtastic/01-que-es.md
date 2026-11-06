# Meshtastic: qué es y cómo funciona

Meshtastic convierte radios LoRa de bajo coste en una red de mensajería que no depende de internet, ni de la cobertura móvil, ni de ningún servidor. Cada equipo es un nodo, y los nodos se retransmiten los mensajes entre ellos.

## LoRa en dos frases

LoRa es una modulación de espectro ensanchado: transmite muy despacio, pero con muy poca potencia y muchísima sensibilidad en recepción. Por eso un módulo de décimas de vatio puede mandar un mensaje a kilómetros, a cambio de que ese mensaje sea corto.

## La malla

Un mensaje no tiene por qué llegar directo. Si el nodo A no oye al nodo C, pero ambos oyen al B, B repite el mensaje y llega. Eso se hace con un número limitado de saltos, para que la red no se sature.

Consecuencias prácticas:

- Cuantos más nodos bien situados, mejor cobertura, aunque estén lejos entre sí.
- Un nodo elevado vale más que varios a ras de suelo.
- Si saturas el canal, perjudicas a todos: la red es compartida.

## Canales y claves

Los nodos se agrupan por canal. Un canal tiene un nombre, un índice y una clave. Solo los equipos con la misma clave se entienden y pueden leer los mensajes.

- El canal principal suele ser público dentro de una comunidad.
- Los canales con clave propia son para grupos cerrados.
- Los mensajes directos van cifrados con la clave del nodo destinatario.

Perder la clave de un canal es quedarse fuera: no hay recuperación, hay que volver a configurar el equipo con la clave correcta.

## Mensajes directos y de canal

- **Canal:** lo reciben todos los nodos del canal. Sirve para coordinarse.
- **Directo:** solo lo lee el destinatario, con acuse de recibo.
- **Posición:** los nodos con GPS comparten su ubicación, a demanda o periódicamente.
- **Telemetría:** batería, voltaje y calidad de señal, de forma automática.

## Límites que conviene aceptar

- **Semidúplex:** un nodo que está oyendo no está hablando. No hay conversaciones simultáneas.
- **Mensajes cortos:** texto y datos pequeños. No hay llamadas, ni fotos, ni vídeo.
- **Tiempo en el aire:** cada mensaje ocupa el canal un rato. Enviar cada minuto satura una red con pocos nodos.
- **Alcance variable:** depende de la altura, los edificios y la antena, no solo de la potencia.

## Diferencia con LoRaWAN

LoRaWAN es una red de estrellas con un servidor central: los nodos hablan con una puerta de enlace, y esa puerta con internet. Meshtastic es malla sin centro: si no hay internet, sigue funcionando. Para sensores sueltos con cobertura de un operador, LoRaWAN; para comunicación entre personas sin infraestructura, Meshtastic.

## Para qué sirve de verdad

- Mensajería en zonas sin cobertura: monte, obras, emergencias.
- Coordinación de grupos en actividades al aire libre.
- Telemetría y posición de vehículos o equipos.
- Red de respaldo cuando cae la red móvil.
- Integración con Home Assistant para recibir avisos en casa.
