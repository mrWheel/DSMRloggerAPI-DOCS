# USE\_PRE40\_PROTOCOL

{% hint style="danger" %}
Vervallen vanaf v3
{% endhint %}

~~De DSMRloggerAPI firmware kan ook overweg met Slimme Meters die nog niet aan de DSMR 4.0 standaard voldoen.~~

{% hint style="danger" %}
~~Let op!  
Deze functionaliteit is slechts beperkt getest!  
Met dank aan Jordy voor het testen met een DSMR 2.2 meter!~~
{% endhint %}

~~Om de DSMRloggerAPI firmware geschikt te maken voor een pré DSMR 4.0 Slimme Meter zijn er een aantal opties mogelijk \(zie de \#define tabel hieronder\) die mogelijk van toepassing zijn op pré DSMR 4.0 Slimme Meters.~~

~~Om deze functionaliteit te kunnen gebruiken moet je ook de speciaal gehackte~~ [~~arduino-dsmr30~~](https://github.com/mrWheel/arduino-dsmr30) ~~bibliotheek installeren!~~

| ~~\#define~~ | ~~Functie~~ |
| :--- | :--- |
| ~~USE\_PRE40\_PROTOCOL~~ | ~~Deze define zorgt ervoor dat de instellingen voor de seriële poort goed worden gezet \(9600, SERIAL\_7E1\). tevens wordt een speciaal gehackte 'arduino-dsmr' bibliotheek gebruikt omdat het pré DSMR 4.0 protocol geen checksum heeft.~~ |
| ~~USE\_NTP\_TIME~~ | ~~Het pré DSMR 4.0 protocol geeft niet altijd een timestamp \(0-0:1.0.0\). Doet jouw Slimme Meter dat ook niet, dan wordt met deze define de tijd via het NTP protocol gebruikt. Vooralsnog alleen Winter Tijd!~~ |

