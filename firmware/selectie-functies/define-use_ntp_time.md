# USE\_NTP\_TIME

{% hint style="danger" %}
Vervallen vanaf v3
{% endhint %}

~~Met deze \#define zorg je ervoor dat de Firmware gebruik maakt van het Network Time Protocol om te bepalen wanneer een Telegram binnen is gekomen. Normaal geeft de Slimme Meter de datum en tijd bij ieder Telegram mee \(in recordtype "0-0:1.0.0"\), maar sommige Slimme Meters doen dat niet \(bijvoorbeeld sommige pré DSMR 4.0 meters\). Deze optie zorgt er dan voor dat alle Telegrammen goed verwerkt worden.~~

{% hint style="warning" %}
~~Let op!  
Gebruik deze optie alléén als je Slimme Meter géén timestamp doorgeeft!!~~
{% endhint %}

| ~~\#define~~ | ~~Functie~~ |
| :--- | :--- |
| ~~USE\_NTP\_TIME~~ | ~~Ieder Telegram wordt gemarkeerd met een via NTP verkregen Timestamp.~~ |

