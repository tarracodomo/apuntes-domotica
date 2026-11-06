# Meshtastic en España y errores frecuentes

## Banda y región

- La banda libre europea es la de **863 a 870 MHz**. Los equipos se compran en versión 868 MHz.
- En la aplicación hay que fijar la región (**EU_868**). Si la región no coincide, los equipos pueden no verse o transmitir donde no deben.
- No hace falta licencia, pero sí respetar los límites de la banda. En Europa el ciclo de trabajo es limitado: el equipo no puede transmitir de forma continua.
- La potencia máxima la fija la región en el firmware. No la subas por encima de lo que permite la ley.

## Lo que hay que tener claro antes de montar

- Es una red compartida: si saturas el canal, perjudicas a todos los nodos cercanos.
- Los mensajes son cortos. Para enviar datos constantes, hay tecnologías mejores.
- La cobertura depende de la altura y los obstáculos, no de la potencia.
- Un nodo que solo repite consume poco y ayuda mucho; no hace falta que tenga pantalla.

## Errores que se repiten

| Problema | Causa habitual | Solución |
|---|---|---|
| Dos nodos no se ven | Región distinta | Fijar la misma región en ambos |
| Se ven pero no se leen los mensajes | Canal o clave distintos | Copiar el mismo canal y clave |
| Alcance muy corto | Antena equivocada o sin antena | Antena de 868 MHz y bien conectada |
| Se reinicia al transmitir | Fuente o batería insuficiente | Fuente que dé la corriente del pico |
| No fija el GPS | Dentro de casa o antena tapada | Probar en exterior, con cielo despejado |
| Batería que dura horas | GPS y pantalla activos | Bajar frecuencia de posición y apagar pantalla |
| La actualización por Bluetooth falla | Distancia o interferencias | Acercarse, o actualizar por USB |
| El equipo arranca pero no emite | Antena mal o radio dañado | Probar con otra antena conocida |

## Cómo comprobar que funciona

1. Enciende dos nodos en la misma habitación, con la misma región y el mismo canal.
2. Espera a que aparezcan en la lista de nodos. Si no aparecen, el problema es de configuración, no de alcance.
3. Aléjalos y observa la calidad de señal en la telemetría.
4. Prueba un mensaje de canal y un mensaje directo con acuse.

Si los dos primeros pasos fallan, no sigas: ningún montaje en el tejado va a arreglar una región mal puesta.

## Integración con Home Assistant

Un nodo conectado a la red WiFi puede enviar los mensajes y las posiciones a Home Assistant, a través de MQTT o de la integración correspondiente. Así los avisos de la malla aparecen en el mismo panel que el resto de la casa, y se pueden usar como disparadores de automatizaciones.

## Aviso

Meshtastic es una marca registrada de sus titulares. Estos apuntes son propios, no oficiales, y no están avalados por el proyecto. Los datos técnicos son orientativos: comprueba siempre la normativa vigente y la documentación oficial antes de instalar un nodo.
