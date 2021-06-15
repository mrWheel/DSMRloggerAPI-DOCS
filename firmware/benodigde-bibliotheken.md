# Installeren benodigde bibliotheken



Voor de **DSMRloggerAPI** firmware zijn de volgende bibliotheken nodig:

#### dsmr2Lib

Deze library is een uitbreiding op de _arduino-dsmr_ van [Matthijs Kooijman](https://github.com/matthijskooijman/arduino-dsmr). Je kunt de dsmr2Lib library [hier](https://github.com/mrWheel/dsmr2Lib) vinden.

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

