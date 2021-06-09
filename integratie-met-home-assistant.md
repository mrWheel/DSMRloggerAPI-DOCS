# Integratie met Home Assistant

Om in Home Assistant de gegevens uit de DSMR-logger \(met de **DSMRloggerAPI** firmware\) te gebruiken heb ik het **`configuration.yaml`** bestand als volgt aangepast:

```text
#################################
# uitbreiding configuratie.yaml #
#################################
# koppeling met de DSMR-logger  #
#################################

sensor:
  - platform: mqtt
    name: "Gebruik"
    state_topic: "DSMR-API/power_delivered" 
    unit_of_measurement: "kWh"
    value_template: '{{ value_json.power_delivered[0].value | round(3) }}'

  - platform: mqtt
    name: "Laatste Update mqtt"
    state_topic: "DSMR-API/timestamp" 
#   value_template: '{{ value_json.timestamp[0].value }}'
    value_template: >
      {{      value_json.timestamp[0].value[4:6] + "-" + 
              value_json.timestamp[0].value[2:4] + "-" + 
         "20"+value_json.timestamp[0].value[0:2] + "   " + 
              value_json.timestamp[0].value[6:8] + ":" + 
              value_json.timestamp[0].value[8:10] + ":" + 
              value_json.timestamp[0].value[10:13] }}

  - platform: mqtt
    name: "Gebruik l1"
    state_topic: "DSMR-API/power_delivered_l1"
    unit_of_measurement: 'Watt'
    value_template: "{{ (value_json.power_delivered_l1[0].value | float * 1000.0) | round(1) }}"

  - platform: mqtt
    name: "Gebruik l2"
    state_topic: "DSMR-API/power_delivered_l2"
    unit_of_measurement: 'Watt'
    value_template: "{{ (value_json.power_delivered_l2[0].value | float * 1000.0) | round(1) }}"

  - platform: mqtt
    name: "Gebruik l3"
    state_topic: "DSMR-API/power_delivered_l3"
    unit_of_measurement: 'Watt'
    value_template: "{{ (value_json.power_delivered_l3[0].value | float * 1000.0) | round(1) }}"


  - platform: rest
    name: "Levering"
    resource: http://192.168.2.106/api/v1/sm/fields/power_returned
    unit_of_measurement: "kWh"
    value_template: '{{ value_json.fields[1].value | round(3) }}'

  - platform: rest
    name: "Laatste Update restAPI"
    resource: http://192.168.2.106/api/v1/sm/fields/timestamp
#   value_template: '{{ value_json.fields[0].value }}'
    value_template: >
      {{      value_json.fields[0].value[4:6] + "-" + 
              value_json.fields[0].value[2:4] + "-" + 
         "20"+value_json.fields[0].value[0:2] + "   " + 
              value_json.fields[0].value[6:8] + ":" + 
              value_json.fields[0].value[8:10] + ":" + 
              value_json.fields[0].value[10:13] }}

  - platform: rest
    name: "Levering l1"
    resource: http://192.168.2.106/api/v1/sm/fields/power_returned_l1
    unit_of_measurement: "Watt"
    value_template: '{{ (value_json.fields[1].value | float * 1000.0) | round(1) }}'

  - platform: rest
    name: "Levering l2"
    resource: http://192.168.2.106/api/v1/sm/fields/power_returned_l2
    unit_of_measurement: 'Watt'
    value_template: '{{ (value_json.fields[1].value | float * 1000.0) | round(1) }}'

  - platform: rest
    name: "Levering l3"
    resource: http://192.168.2.106/api/v1/sm/fields/power_returned_l3
    unit_of_measurement: 'Watt'
    value_template: '{{ (value_json.fields[1].value | float * 1000.0) | round(1) }}'
```

Optioneel: Gas gebruik toevoegen \(let op: is totaal gebruik\):

```text
  - platform: mqtt
    name: "Gas gebruik"
    state_topic: "DSMR-API/gas_delivered"
    unit_of_measurement: 'm3'
    value_template: "{{ (value_json.gas_delivered[0].value | float * 1000.0) | round(1) }}"
```

in deze voorbeelden worden de power\_delivered en gas\_delivered velden via MQTT uitgelezen en de power\_returned via de restAPI's. Uiteraard kun je voor alle velden de manier van uitlezen gebruiken die voor jou het prettigste werkt.

Dit is het resultaat:

![](.gitbook/assets/ha_integratie.png)

{% hint style="warning" %}
Merk op dat ik voor de resource bij de restAPI's het IP adres van de DSMR-logger gebruik. Ik krijg het in mijn opzet niet voor elkaar hier de hostname \(dsmr-api.local\) te gebruiken. Controleer ook of het MQTT topic juist is.
{% endhint %}

