# Slimme Meter gerelateerde restAPI's

{% api-method method="get" host="http://dsmr-api.local" path="/api/v1/sm/info" %}
{% api-method-summary %}
Systeem Informatie van de Slimme Meter
{% endapi-method-summary %}

{% api-method-description %}
Geeft systeem een JSON string met informatie van de Slimme Meter, zoals ID's en Serie nummers, terug.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Succes
{% endapi-method-response-example-description %}

```
{"info":[
  {"name": "identification", "value": "XMX5LABCDB2410065887"},
  {"name": "p1_version", "value": "50"},
  {"name": "equipment_id", "value": "4530303336303000000000000000000040"},
  {"name": "electricity_tariff", "value": "0001"},
  {"name": "mbus1_device_type", "value": 3},
  {"name": "mbus1_equipment_id_tc", "value": "4730303339303031363532303530323136"},
  {"name": "mbus4_device_type", "value": 5},
  {"name": "mbus4_equipment_id_tc", "value": "4730303339303031344444444444444444"}
]}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://dsmr-api.local" path="/api/v1/sm/actual" %}
{% api-method-summary %}
Informatie uit het laatst gelezen telegram
{% endapi-method-summary %}

{% api-method-description %}
Geeft de actuele meterstanden van de Slimme Meter terug in een JSON string.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Succes
{% endapi-method-response-example-description %}

```
{"actual":[
  {"name": "timestamp", "value": "210419050001S"},
  {"name": "energy_delivered_tariff1", "value": 2332.511, "unit": "kWh"},
  {"name": "energy_delivered_tariff2", "value": 8514.767, "unit": "kWh"},
  {"name": "energy_returned_tariff1", "value": 353.841, "unit": "kWh"},
  {"name": "energy_returned_tariff2", "value": 196.645, "unit": "kWh"},
  {"name": "power_delivered", "value": 1.880, "unit": "kW"},
  {"name": "power_returned", "value": 0.000, "unit": "kW"},
  {"name": "voltage_l1", "value": 239.000, "unit": "V"},
  {"name": "voltage_l2", "value": 236.000, "unit": "V"},
  {"name": "voltage_l3", "value": 237.000, "unit": "V"},
  {"name": "current_l1", "value": 3, "unit": "A"},
  {"name": "current_l2", "value": 0, "unit": "A"},
  {"name": "current_l3", "value": 0, "unit": "A"},
  {"name": "power_delivered_l1", "value": 0.500, "unit": "kW"},
  {"name": "power_delivered_l2", "value": 0.899, "unit": "kW"},
  {"name": "power_delivered_l3", "value": 0.480, "unit": "kW"},
  {"name": "power_returned_l1", "value": 0.000, "unit": "kW"},
  {"name": "power_returned_l2", "value": 0.000, "unit": "kW"},
  {"name": "power_returned_l3", "value": 0.000, "unit": "kW"},
  {"name": "gas_delivered", "value": 2963.380, "unit": "m3"}
]}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://dsmr-api.local" path="/api/v0/sm/actual" %}
{% api-method-summary %}
Informatie uit het laatst gelezen telegram
{% endapi-method-summary %}

{% api-method-description %}
Deze api dient voor backwards compatibility met de _DSMRloggerWS_ firmware. Deze api call geeft de actuele informatie van de Slimme Meter terug in een JSON string.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "timestamp": "170102105001S",
  "energy_delivered_tariff1": 146.380,
  "energy_delivered_tariff2": 70.511,
  "energy_returned_tariff1": 111.164,
  "energy_returned_tariff2": 75.530,
  "power_delivered": 1.750,
  "power_returned": 1.270,
  "voltage_l1": 242.000,
  "voltage_l2": 240.000,
  "voltage_l3": 234.000,
  "current_l1": 0,
  "current_l2": 0,
  "current_l3": 0,
  "power_delivered_l1": 1.046,
  "power_delivered_l2": 0.464,
  "power_delivered_l3": 0.243,
  "power_returned_l1": 0.669,
  "power_returned_l2": 0.521,
  "power_returned_l3": 0.078,
  "gas_delivered": 100.550
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://dsmr-api.local" path="/api/v1/sm/fields" %}
{% api-method-summary %}
Alle velden die de dsmr library terug kan geven
{% endapi-method-summary %}

{% api-method-description %}
Geeft een JSON string met alle velden die door de DSMRloggerAPI firmware kunnen worden terug gegeven.   
**Let op!** Niet iedere Slimme Meter geeft ook al deze velden terug. Als de Slimme meter een veld niet terug geeft heeft `"value"` de waarde **`"-"`**.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Sucess
{% endapi-method-response-example-description %}

```
{"fields":[
  {"name": "identification", "value": "XYZ12345678909897654"},
  {"name": "p1_version", "value": "50"},
  {"name": "p1_version_be", "value": "-"},
  {"name": "timestamp", "value": "210610103351S"},
  {"name": "equipment_id", "value": "45303033363030333754321098765"},
  {"name": "energy_delivered_tariff1", "value": 4491.266, "unit": "kWh"},
  {"name": "energy_delivered_tariff2", "value": 6065.275, "unit": "kWh"},
  {"name": "energy_returned_tariff1", "value": 788.990, "unit": "kWh"},
  {"name": "energy_returned_tariff2", "value": 1809.853, "unit": "kWh"},
  {"name": "electricity_tariff", "value": "0002"},
  {"name": "power_delivered", "value": 0.000, "unit": "kW"},
  {"name": "power_returned", "value": 1.023, "unit": "kW"},
  {"name": "electricity_threshold", "value": "-"},
  {"name": "electricity_switch_position", "value": "-"},
  {"name": "electricity_failures", "value": 11},
  {"name": "electricity_long_failures", "value": 1},
  {"name": "electricity_failure_log", "value": "(1)(0-0:96.7.19)(200210104719W)(0000014540*s)"},
  {"name": "electricity_sags_l1", "value": 10},
  {"name": "electricity_sags_l2", "value": 7},
  {"name": "electricity_sags_l3", "value": 9},
  {"name": "electricity_swells_l1", "value": 0},
  {"name": "electricity_swells_l2", "value": 0},
  {"name": "electricity_swells_l3", "value": 0},
  {"name": "message_short", "value": "-"},
  {"name": "message_long", "value": ""},
  {"name": "voltage_l1", "value": 235.000, "unit": "V"},
  {"name": "voltage_l2", "value": 238.000, "unit": "V"},
  {"name": "voltage_l3", "value": 239.000, "unit": "V"},
  {"name": "current_l1", "value": 0.000, "unit": "A"},
  {"name": "current_l2", "value": 0.000, "unit": "A"},
  {"name": "current_l3", "value": 5.000, "unit": "A"},
  {"name": "power_delivered_l1", "value": 0.075, "unit": "kW"},
  {"name": "power_delivered_l2", "value": 0.106, "unit": "kW"},
  {"name": "power_delivered_l3", "value": 0.000, "unit": "kW"},
  {"name": "power_returned_l1", "value": 0.000, "unit": "kW"},
  {"name": "power_returned_l2", "value": 0.000, "unit": "kW"},
  {"name": "power_returned_l3", "value": 1.205, "unit": "kW"},
  {"name": "mbus1_device_type", "value": 3},
  {"name": "mbus1_equipment_id_tc", "value": "47303044449303031363532309876543211"},
  {"name": "mbus1_equipment_id_ntc", "value": "-"},
  {"name": "mbus1_valve_position", "value": "-"},
  {"name": "mbus1_delivered", "value": 3845.379, "unit": "m3"},
  {"name": "mbus1_delivered_ntc", "value": "-"},
  {"name": "mbus1_delivered_dbl", "value": "-"},
  {"name": "mbus2_device_type", "value": "-"},
  {"name": "mbus2_equipment_id_tc", "value": "-"},
  {"name": "mbus2_equipment_id_ntc", "value": "-"},
  {"name": "mbus2_valve_position", "value": "-"},
  {"name": "mbus2_delivered", "value": 0.000, "unit": "GJ"},
  {"name": "mbus2_delivered_ntc", "value": "-"},
  {"name": "mbus2_delivered_dbl", "value": "-"},
  {"name": "mbus3_device_type", "value": "-"},
  {"name": "mbus3_equipment_id_tc", "value": "-"},
  {"name": "mbus3_equipment_id_ntc", "value": "-"},
  {"name": "mbus3_valve_position", "value": "-"},
  {"name": "mbus3_delivered", "value": 0.000, "unit": "m3"},
  {"name": "mbus3_delivered_ntc", "value": "-"},
  {"name": "mbus3_delivered_dbl", "value": "-"},
  {"name": "mbus4_device_type", "value": "-"},
  {"name": "mbus4_equipment_id_tc", "value": "-"},
  {"name": "mbus4_equipment_id_ntc", "value": "-"},
  {"name": "mbus4_valve_position", "value": "-"},
  {"name": "mbus4_delivered", "value": 0.000, "unit": "m3"},
  {"name": "mbus4_delivered_ntc", "value": "-"},
  {"name": "mbus4_delivered_dbl", "value": "-"}
]}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://dsmr-api.local" path="/api/v1/sm/fields/<fieldName>" %}
{% api-method-summary %}
Informatie van één veld uit het laatst gelezen telegram
{% endapi-method-summary %}

{% api-method-description %}
Geeft een JSON string met informatie over één veld terug. Bijvoorbeeld:  
  
http://dsmr-api.local/api/v1/sm/fields/current\_l2
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{"fields":[
  {"name": "timestamp", "value": "210315080001S"},
  {"name": "current_l2", "value": 1, "unit": "A"}
]}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="http://dsmr-api.local" path="/api/v1/sm/telegram" %}
{% api-method-summary %}
Onbewerkt telegram uit de Slimme Meter
{% endapi-method-summary %}

{% api-method-description %}
Geeft een telegram terug precies zo als de Slimme Meter die ook afgeeft, dus inclusief "\r\n" line endings en inclusief de CheckSum!
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Succes
{% endapi-method-response-example-description %}

```
/XMX5LABCDE2410065447

1-3:0.2.8(50)
0-0:1.0.0(210610104031S)
0-0:96.1.1(4530304446303033373839312345678906)
1-0:1.8.1(004491.266*kWh)
1-0:1.8.2(006065.310*kWh)
1-0:2.8.1(000788.990*kWh)
1-0:2.8.2(001809.893*kWh)
0-0:96.14.0(0002)
1-0:1.7.0(00.037*kW)
1-0:2.7.0(00.000*kW)
0-0:96.7.21(00011)
0-0:96.7.9(00001)
1-0:99.97.0(1)(0-0:96.7.19)(200210104719W)(0000014540*s)
1-0:32.32.0(00010)
1-0:52.32.0(00007)
1-0:72.32.0(00009)
1-0:32.36.0(00000)
1-0:52.36.0(00000)
1-0:72.36.0(00000)
0-0:96.13.0()
1-0:32.7.0(238.0*V)
1-0:52.7.0(238.0*V)
1-0:72.7.0(238.0*V)
1-0:31.7.0(002*A)
1-0:51.7.0(000*A)
1-0:71.7.0(003*A)
1-0:21.7.0(00.598*kW)
1-0:41.7.0(00.102*kW)
1-0:61.7.0(00.000*kW)
1-0:22.7.0(00.000*kW)
1-0:42.7.0(00.000*kW)
1-0:62.7.0(00.663*kW)
0-1:24.1.0(003)
0-1:96.1.0(4730305559303031363839312345678906)
0-1:24.2.1(210610104007S)(03845.376*m3)
!344A

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

