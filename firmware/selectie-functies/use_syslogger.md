# USE\_SYSLOGGER

{% hint style="danger" %}
Deze functionaliteit is in versie 3 nog niet getest.  
Deze nieuwe versie maakt geen gebruik meer van SPIFFS maar gebruikt van het LittleFS. De SysLogger is hier nog niet voor aangepast!
{% endhint %}

Als deze optie actief is zal de DSMRloggerAPI firmware debug informatie naar een logfile schrijven. Dit logfile kan mbv.het commando 'Q' in het telnet menu bekeken worden.

Er is ook een restAPI waarmee de log regels uit de DSMR-logger opgehaald kunnen worden.

{% api-method method="get" host="http://dsmr-api.local" path="/api/v1/dev/debug" %}
{% api-method-summary %}
Ophalen debug informatie
{% endapi-method-summary %}

{% api-method-description %}
Met deze api kun je de gegevens uit het sysLog bestand opvragen
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
**
***************************************************************************************************
***************************************************************************************************
***************************************************************************************************
[15:23:35][  12624][openSysLog  ] Last Reset Reason [Software/System restart]
[15:23:35][  13968][openSysLog  ] actTimestamp[200316152328W], nrReboots[0], Errors[0]
 
[15:24:05][  12640][forceMinderg] Force Write Data to [/Mindergas.post]
[15:24:05][  12640][processMinde] Mindergas State: MG_WRITE_TO_FILE
[15:24:05][  12640][writePostToF] Writing to [/Mindergas.post] ..
[15:24:05][  12640][writePostToF] Mindergas.post aangemaakt
[15:24:05][  12640][writePostToF] MinderGas update in [118] minute(s)
[15:25:05][  12496][processMinde] Mindergas State: MG_DO_COUNTDOWN (118 minuten te gaan)
[15:26:05][  12480][processMinde] Mindergas State: MG_DO_COUNTDOWN (117 minuten te gaan)
[15:26:50][  12216][processSlimm] Processed [25] telegrams ([0] errors)
[15:27:05][  12672][processMinde] Mindergas State: MG_DO_COUNTDOWN (116 minuten te gaan)
[15:28:05][  12688][processMinde] Mindergas State: MG_DO_COUNTDOWN (115 minuten te gaan)
    .
    .
    .
[15:39:05][  12688][processMinde] Mindergas State: MG_DO_COUNTDOWN (104 minuten te gaan)
[15:40:05][  12672][processMinde] Mindergas State: MG_DO_COUNTDOWN (103 minuten te gaan)
[15:40:10][  10632][processSlimm] Processed [125] telegrams ([0] errors)
[15:41:05][  12688][processMinde] Mindergas State: MG_DO_COUNTDOWN (102 minuten te gaan)
[15:42:05][  12688][processMinde] Mindergas State: MG_DO_COUNTDOWN (101 minuten te gaan)
[15:43:05][  12688][processMinde] Mindergas State: MG_DO_COUNTDOWN (100 minuten te gaan)
[15:43:30][  12000][processSlimm] Processed [150] telegrams ([0] errors)
[15:44:05][  12688][processMinde] Mindergas State: MG_DO_COUNTDOWN (99 minuten te gaan)
[15:45:05][  14264][processMinde] Mindergas State: MG_DO_COUNTDOWN (98 minuten te gaan)
[15:46:05][  14280][processMinde] Mindergas State: MG_DO_COUNTDOWN (97 minuten te gaan)
[15:46:50][  12920][processSlimm] Processed [175] telegrams ([0] errors)
[15:47:05][  14280][processMinde] Mindergas State: MG_DO_COUNTDOWN (96 minuten te gaan)
[15:48:05][  14280][processMinde] Mindergas State: MG_DO_COUNTDOWN (95 minuten te gaan)
[15:49:05][  14280][processMinde] Mindergas State: MG_DO_COUNTDOWN (94 minuten te gaan)
[15:50:05][  14032][processMinde] Mindergas State: MG_DO_COUNTDOWN (93 minuten te gaan)
[15:50:10][  12920][processSlimm] Processed [200] telegrams ([0] errors)
    .
    .
    .
[15:57:05][  14264][processMinde] Mindergas State: MG_DO_COUNTDOWN (2 minuten te gaan)
[15:58:34][  13744][forceMinderg] found [/Mindergas.post] at day#[16]
[15:58:34][  12400][processMinde] Mindergas State: MG_DO_COUNTDOWN (1 minuten te gaan)
[15:59:34][  12184][processMinde] Mindergas State: MG_SEND_MINDERGAS
[15:59:34][  11672][sendMinderga] Send to Mindergas.nl...
POST /api/gas_meter_readings HTTP/1.1**AUTH-TOKEN:<token>**Host: mindergas.nl**User-Ag
[15:59:35][  12360][sendMinderga] Mindergas response: [422]
Unprocessed entity, goto website mindergas for more information
[15:59:35][  11208][sendMinderga] Disconnected from mindergas.nl
[15:59:35][  12184][processMinde] Deleted Mindergas.post !
[16:00:03][  11000][processTeleg] Update RING-files
[16:00:11][  10368][processSlimm] Processed [275] telegrams ([0] errors)
[16:03:31][  11160][processSlimm] Processed [300] telegrams ([0] errors)
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

| \#define | Functie |
| :--- | :--- |
| USE\_SYSLOGGER | De ESP\_SysLogger is een library waarmee log regels in een RING bestand van 500 regels kunnen worden geschreven. Na 500 regels wordt steeds de oudste regel overschreven door de nieuwste regel. |

