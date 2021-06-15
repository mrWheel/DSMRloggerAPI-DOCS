# USE\_UPDATE\_SERVER

Met deze optie wordt het mogelijk om nieuwe Firmware naar de DSMR-logger te flashen door in de FSmanager op de knop **`[Update Firmware]`** te klikken.

![](../../.gitbook/assets/screenshot-2021-06-09-at-14.03.47.png)

en vervolgens in de Flash Utility ..

![](../../.gitbook/assets/screenshot-2021-06-10-at-10.13.14.png)

.. op **`[Choose file]`** te klikken en daarna op **`[Flash Firmware]`**

{% hint style="info" %}
Let op!   
Deze functionaliteit werkt alleen als je 4MB flash geheugen hebt. Standaard heeft iedere ESP-12 dat en dus ook de DSMR-logger v4 of v4.5.  
Je kunt een ESP-01 eventueel upgraden naar 4MB door de aanwezige flash chip te vervangen door een W25Q32FVSIG 32Mbit flash chip.
{% endhint %}

| \#define | Functie |
| :--- | :--- |
| USE\_UPDATE\_SERVER | Om gebruik te kunnen maken van zgn. "Over The Air" \(OTA\) updates van de firmware en het bestand systeem moet je deze optie activeren \(default\). Dit kan alleen met een ESP-12 of een, met **4MB chip ge-upgrade** ESP-01 bordjes! '**Normale**' \(1MB\) ESP-01 bordjes hebben hier niet genoeg flash-geheugen voor. |

