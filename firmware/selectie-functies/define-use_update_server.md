# USE\_UPDATE\_SERVER

Met deze optie wordt het mogelijk om nieuwe Firmware naar de DSMR-logger te flashen door in de FSexplorer op de knop `[Update Firmware]` te klikken

![](https://mrwheel.github.io/DSMRloggerWS/img/DSMRloggerWS_FSexplorer.png)

en vervolgens in de Flash Utility ..

![](https://mrwheel.github.io/DSMRloggerWS/img/DSMR-logger_FlashUtility.png)

.. op `[Choose file]` te klikken en daarna op `[Flash Firmware]`

{% hint style="info" %}
Let op!   
Alleen voor ESP-12 Deze functionaliteit werkt alleen als je 4MB flash geheugen hebt. Standaard heeft iedere ESP-12 dat.  
Je kunt een ESP-01 eventueel upgraden naar 4MB door de aanwezige flash chip te vervangen door een W25Q32FVSIG 32Mbit flash chip.
{% endhint %}

| \#define | Functie |
| :--- | :--- |
| USE\_UPDATE\_SERVER | Om gebruik te kunnen maken van zgn. "Over The Air" \(OTA\) updates van de firmware en het SPIFFS file systeem moet je deze optie activeren. Dit kan alleen met een ESP-12 of een, met **4MB chip ge-upgrade** ESP-01 bordjes! '**Normale**' \(1MB\) ESP-01 bordjes hebben hier niet genoeg flash-geheugen voor. |

