# ESP8266 Core

### Installatie ESP8266 core <a id="installatie-esp8266-core"></a>

In de Arduino IDE moet bij “Instellingen” de volgende URL worden ingevoerd achter “_Additional Boards Manager URL’s:_” \(zie rood omlijnde kader\)

**`https://arduino.esp8266.com/stable/package_esp8266com_index.json`**

![](https://mrwheel.github.io/DSMRloggerWS/img/Preferences.png)

Lees vooral de uitleg in het [`README.md`](https://github.com/esp8266/Arduino/blob/master/README.md) bestand en de uitgebreide [`documentatie`](https://arduino-esp8266.readthedocs.io/en/latest/) op hun website!

Er kunnen meer additional board manager URL’s worden ingevuld. Je moet ze dan achter elkaar zetten en scheiden door een komma \(**,**\).

Eventueel kun je ook het pad waar je projecten staan \(de `Sketchbook Location`\) aanpassen. Standaard verwijst deze naar je `Documenten` map:

**`C:\Users\<YourLoginName>\Documents\arduino\`**

.. en dat is een prima plek!

De andere instellingen kun je naar behoefte aanpassen. Hierboven staan de instellingen die ik prettig vind.

Na het maken van aanpassingen klik je op `[OK]`.

Ga nu via de ArduinoIDE menu-balk naar **`[tools]`**-&gt; **`[Board]`** -&gt; **`[Boards Manager]`**.

![](https://mrwheel.github.io/DSMRloggerWS/img/IDE_BoardsManager.png)

Voer bij filter “esp8266” in.

![](https://mrwheel.github.io/DSMRloggerWS/img/IDE_UpdateInstallESP8266core.png)

Selecteer de versie die je wilt gaan gebruiken en klik op **`[Install]`**.

{% hint style="warning" %}
Let op! De DSMRloggerAPI firmware is getest met **versie 2.7.4** van de Arduino/ESP8266 core. Nieuwere versies zullen zeer waarschijnlijk ook werken, maar bij problemen is het het beste om deze versie te gebruiken.
{% endhint %}

  


