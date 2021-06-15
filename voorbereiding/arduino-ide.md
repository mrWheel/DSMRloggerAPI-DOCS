# Arduino IDE

### Installatie ArduinoIDE <a id="installatie-arduinoide"></a>

Download en installeer de meest actuele versie van de Arduino Integrated Development Environment \(IDE\) voor het Operating Systeem \(OS\) waar jouw Desktop of Laptop computer \(er zijn versies voor Windows, Linux en Mac\) mee werkt.  
Je kunt de Software [hier](https://www.arduino.cc/en/Main/Software) downloaden.

![](https://mrwheel.github.io/DSMRloggerWS/img/DownloadIDE.png)

{% hint style="info" %}
De DSMRloggerAPI firmware is getest met de ArduinoIDE v1.8.13
{% endhint %}

{% hint style="danger" %}
Let op!  
De Arduino IDE v1.9.x \(Beta\) is NIET geschikt om deze firmware mee te compileren.  
Tot v1.9.x zorgt de IDE ervoor dat alle tab-bladen \(**.ino** files\) achter elkaar worden geplakt tot één source file waarna van alle functies in dit gecombineerde file zgn. prototypes worden gemaakt voordat deze aan de compiler \(als één file dus\) wordt aangeboden. De Arduino IDE is eigenlijk de enige IDE \(voor zover ik weet\) die dit doet en is als zodanig dus een beetje vreemd.  
v1.9.x \(Beta\) doet dit voor AVR processoren wel maar helaas \(nog\) niet voor de ESP8266 processor familie.
{% endhint %}

Na het downloaden moet je het ontvangen bestand uitpakken \(unzip of untar\) en installeren. Dat installeren is per OS anders maar staat duidelijk op de website van Arduino aangegeven. Eenmaal geïnstalleerd kun je direct met de Arduino IDE aan de slag.

Om de IDE met de ESP8266 microprocessor te kunnen gebruiken moeten we nog wat stappen uitvoeren.

