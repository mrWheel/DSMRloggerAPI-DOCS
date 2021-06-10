# Installeren benodigde bibliotheken



Voor de **DSMRloggerAPI** firmware zijn de volgende bibliotheken nodig:

#### ~~arduino-dsmr~~ <a id="dsmr"></a>

~~Deze library is ontwikkeld door _Matthijs Kooijman_ en vormt het hart van de DSMR-logger. Je kunt de bibliotheek~~ [~~hier~~](%20https://github.com/matthijskooijman/arduino-dsmr) ~~downloaden.  
De firmware is getest met `Version 0.1 - Commit f79c906 on 18 Sep 2018` maar nieuwere versies zullen waarschijnlijk ook werken.~~

#### ~~arduino-dsmr-be \(_optioneel_\)~~

~~**Let op!** Deze functionaliteit is slechts beperkt getest!~~

~~Dit is een clone van de _**arduino-dsmr**_ bibliotheek van _Matthijs Kooijman_ die is aangepast voor de specifieke Belgische velden. Je kunt deze bibliotheek~~ [~~hier~~](https://github.com/mrWheel/arduino-dsmr-be) ~~downloaden.  
Kijk ook~~ [~~hier~~](selectie-functies/define-use_belgium_protocol.md)~~.~~

#### ~~arduino-dsmr30 \(_optioneel_\)~~ <a id="dsmr30"></a>

~~**Let op!** Deze functionaliteit is slechts beperkt getest!~~

~~Heb je een pré DSMR 4.0 Slimme Meter dan kun je deze toch aansluiten op de DSMR-logger maar moet je een aantal `#define`'s in het eerste tab-blad aanpassen én je moet~~ [~~deze~~](https://github.com/mrWheel/arduino-dsmr30) ~~library installeren. Kijk ook~~ [~~hier~~](selectie-functies/define-use_pre40_protocol.md)~~.~~

#### dsmr2Lib

Deze library is een combinatie van de drie voorgaande libraries \(arduino-dsmr, arduino-dsmr-be en arduino-dsmr30\). Je kunt de library [hier](https://github.com/mrWheel/dsmr2Lib) vinden.

#### TimeLib <a id="timelib"></a>

Deze is door _Paul Stoffregen_ ontwikkeld. Je kunt hem [hier](https://github.com/PaulStoffregen/Time) downloaden.

#### WiFiManager <a id="wifimanager"></a>

Je kunt de, door _Tzapu_ ontwikkelde, bibliotheek [hier](https://github.com/tzapu/WiFiManager) downloaden.  
De DSMR-logger firmware is getest met `version 0.14.0` van deze bibliotheek maar nieuwere versies zullen waarschijnlijk ook werken.

#### TelnetStream <a id="telnetstream"></a>

Deze bibliotheek is door _Juraj Andrassy_ ontwikkeld. Je kunt deze bibliotheek [hier](https://github.com/jandrassy/TelnetStream) downloaden.  
De firmware is getest met `version 0.0.1` maar nieuwere versies zullen waarschijnlijk ook werken.

{% hint style="warning" %}
**Let op:**   
De installatie van deze bibliotheek gaat net als de andere bibliotheken. Een update kan echter pas geïnstalleerd worden als éérst de map `TelnetStream-master` uit de map `Libraries` wordt verwijderd!
{% endhint %}

#### SSD1306Ascii <a id="ssd1306ascii"></a>

_William Greiman_ heeft deze bibliotheek ontwikkeld met in het achterhoofd minimaal gebruik van resources \(dus: een bibliotheek die weinig geheugen gebruikt\). Je kunt de bibliotheek [hier](https://github.com/greiman/SSD1306Ascii) downloaden.  
De DSMR-logger Firmware is getest met `Version 1.2.x - Commit 97a05cd on 24 Mar 2019` maar nieuwere versies zullen waarschijnlijk ook werken.

#### PubSubClient <a id="pubsubclient"></a>

_Nick O'Leary \(knolleary\)_ heeft deze bibliotheek ontwikkeld. Je kunt de bibliotheek [hier](https://github.com/knolleary/pubsubclient) downloaden.

#### ModUpdateServer <a id="modupdateserver"></a>

Deze bibliotheek maakt het mogelijk om firmware en SPIFFS Over The Air te flashen naar de DSMR-logger.  
Deze bibliotheek is nodig vanaf versie 2.6.2 van de Arduino/ESP8266 core. Je kunt de bibliotheek [hier](https://github.com/mrWheel/ModUpdateServer) downloaden.

#### ESP\_SysLogger

Deze bibliotheek is alleen nodig als je USE\_SYSLOGGER defined. Je kunt de bibliotheek [hier](https://github.com/mrWheel/ESP_SysLogger) downloaden \(vanaf v1.6.3 commit [43eb15681125442addaf8b697f2b8557d4afa300](https://github.com/mrWheel/ESP_SysLogger/commit/43eb15681125442addaf8b697f2b8557d4afa300)\).  
**Pas op!** \(nog\) Niet geschikt voor het LittleFS!

#### Overige libraries <a id="overige-libraries"></a>

Onderstaande libraries zijn onderdeel van de `ESP8266 Core` en moeten dus **niet** handmatig geïnstalleerd worden!

* LittleFS
* ESP8266WiFi
* ESP8266WebServer
* WiFiUdp
* ESP8266mDNS
* FS

