# Automatizaciones

Una automatización tiene tres partes: qué la dispara, qué condición debe cumplirse y qué hace.

## Ejemplo: luz del pasillo con movimiento

```yaml
alias: Luz del pasillo con movimiento
trigger:
  - platform: state
    entity_id: binary_sensor.pasillo_motion
    to: "on"
condition:
  - condition: numeric_state
    entity_id: sensor.luz_pasillo
    below: 60
action:
  - service: light.turn_on
    target:
      entity_id: light.pasillo
    data:
      brightness_pct: 60
  - delay: "00:02:00"
  - service: light.turn_off
    target:
      entity_id: light.pasillo
mode: single
```

La condición de luminosidad evita que la luz se encienda a mediodía. El `mode: single` impide que se acumulen ejecuciones si el sensor salta varias veces.

## Esperar a que deje de haber movimiento

Mejor que un `delay` fijo es esperar a que el sensor se apague, con un tiempo máximo:

```yaml
action:
  - service: light.turn_on
    target:
      entity_id: light.pasillo
  - wait_for_trigger:
      - platform: state
        entity_id: binary_sensor.pasillo_motion
        to: "off"
    timeout: "00:10:00"
    continue_on_timeout: true
  - delay: "00:00:30"
  - service: light.turn_off
    target:
      entity_id: light.pasillo
```

## Plantillas

Sirven para calcular valores sin instalar nada:

```yaml
sensor:
  - platform: template
    sensors:
      consumo_total:
        friendly_name: Consumo total
        unit_of_measurement: W
        value_template: >-
          {{ states('sensor.cocina_power') | float(0)
             + states('sensor.salon_power') | float(0) }}
```

El `float(0)` evita que la plantilla falle cuando un sensor no está disponible, que es la causa número uno de errores en el registro.

## Consejos

- Pon un `id` a cada automatización si vas a activarla o desactivarla por código.
- Nombra las entidades en castellano desde el principio; renombrarlas después rompe las referencias.
- Antes de complicar una automatización, prueba los disparadores con la pestaña de trazas, que muestra por dónde ha pasado y dónde se ha parado.
- Las escenas agrupan estados de varias luces y se aplican de golpe. Para ambientes, ahorran muchas líneas.
