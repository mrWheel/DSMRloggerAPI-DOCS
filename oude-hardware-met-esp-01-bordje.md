# Oude Hardware \(met ESP-01 bordje\)

Het is mogelijk om de nieuwe DSMRloggerAPI firmware geschikt te maken voor de DSMR-logger V3 hardware. Een deel van de functionaliteit, zoals Over The Air updaten, kun je dan echter niet gebruiken.

Om de DSMRloggerAPI firmware geschikt te maken voor de DSMR-logger V3 moet je de volgende instellingen gebruiken:

```text
/******************** compiler options  ********************************************/
//#define USE_REQUEST_PIN           // NIET VOOR EEN V3 BORDJE
//#define USE_UPDATE_SERVER         // (v3)NIET GEBRUIKEN
//  #define USE_BELGIUM_PROTOCOL      // define if Slimme Meter is a Belgium Smart Meter
//  #define USE_PRE40_PROTOCOL        // define if Slimme Meter is pre DSMR 4.0 (2.2 .. 3.0)
//  #define USE_NTP_TIME              // define to generate Timestamp from NTP (Only Winter Time for now)
//  #define HAS_NO_SLIMMEMETER        // define for testing only!
#define USE_MQTT                  // define if you want to use MQTT (configure through webinterface)
//  #define USE_MINDERGAS             // (v3) NIET GETEST!
//  #define USE_SYSLOGGER             // (v3) NIET GEBRUIKEN
//  #define SHOW_PASSWRDS             // well .. show the PSK key and MQTT password, what else?
/******************** don't change anything below this comment **********************/

```

Afhankelijk van je situatie kunnen USE\_BELGIUM\_PROTOCOL, USE\_PRE40\_PROTOCOL, USE\_NTP\_TIME uiteraard wel gebruikt worden.

De compiler instellingen voor de v3 \(met ESP-01\) moeten als volgt staan:

```text
  Arduino-IDE settings for DSMR-logger Version 3 (ESP-01):

    - Board: "Generic ESP8266 Module"
    - Buildin Led: "2"  // GPIO02 for Wemos and ESP-12 and ESP-01 Black
    - Flash mode: "DOUT" | "DIO"    // change only after power-off and on again!
    - Flash size: "1MB (FS: 256KB OAT:~374KB)"  << LET OP! 256KB SPIFFS
    - DebugT port: "Disabled"
    - DebugT Level: "None"
    - IwIP Variant: "v2 Lower Memory"
    - Reset Method: "none"   // but will depend on the programmer!
    - Crystal Frequency: "26 MHz" 
    - VTables: "Flash"
    - Flash Frequency: "40MHz"
    - CPU Frequency: "80 MHz" (or 160MHz)
    - Upload Speed: "115200"                                                                                                                                                                                                                                                 
    - Erase Flash: "Only Sketch"
    - Port: <select correct port>

```

