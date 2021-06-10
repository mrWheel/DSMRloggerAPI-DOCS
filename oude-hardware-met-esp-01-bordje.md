# Oude Hardware \(met ESP-01 bordje\)

{% hint style="danger" %}
De omvang van de DSMTloggerAPI firmware is te groot geworden voor een ESP-01 bordje. Het is wél mogelijk om de 1MB flash chip van de ESP-01 te vervangen door een 4MB flash chip, waarna er wél voldoende ruimte is voor deze firmware!
{% endhint %}

~~Het is mogelijk om de nieuwe DSMRloggerAPI firmware geschikt te maken voor de DSMR-logger V3 hardware. Een deel van de functionaliteit, zoals _Over The Air updaten_, kun je dan echter niet gebruiken.~~

~~Om de DSMRloggerAPI firmware geschikt te maken voor de DSMR-logger V3 moet je de volgende instellingen gebruiken:~~

```text
/******************** compiler options  ********************************************/
//  #define HAS_NO_SLIMMEMETER        // define for testing only!
#define USE_MQTT                  // define if you want to use MQTT (configure through webinterface)
//  #define SHOW_PASSWRDS             // well .. show the PSK key and MQTT password, what else?
/******************** don't change anything below this comment **********************/

```

~~Afhankelijk van je situatie kunnen USE\_BELGIUM\_PROTOCOL, USE\_PRE40\_PROTOCOL en/of USE\_NTP\_TIME uiteraard wel gebruikt worden.~~

~~De compiler instellingen voor de v3 \(met ESP-01\) moeten als volgt staan:~~

```text
  Arduino-IDE settings for DSMR-logger Version 3 (ESP-01):

    - Board: "Generic ESP8266 Module"
    - Buildin Led: "2"  // GPIO02 for Wemos and ESP-12 and ESP-01 Black
    - Flash mode: "DOUT" | "DIO"    // change only after power-off and on again!
    - You cannot flash this firmware to an ESP-01 board                                                                                                                                                                                                                                                 
    - Erase Flash: "Only Sketch"
    - Port: <select correct port>

```

