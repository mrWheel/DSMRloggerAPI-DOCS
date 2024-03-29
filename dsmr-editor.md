# DSMR-editor

De DSMRloggerAPI heeft de mogelijkheid om meterstanden en instellingen via de browser te veranderen.

Je start de **`DSMR-editor`** door in het hoofdscherm op het ![](.gitbook/assets/settingsicoon.png) icoontje te klikken.

![](.gitbook/assets/settingseditorstart.png)

Betekenis van de knoppen:

* **Terug**: Terug naar het hoofdscherm van de DSMR-logger
* **Meterstanden**: Hier kunnen, per maand, de meterstanden worden ingevoerd. Er kan gekozen worden tussen de meterstanden van de gebruikte energie, de opgewekte energie en het gas verbruik.
* **Settings**: Hier kunnen bepaalde parameters zoals de energie tarieven, interval voor het lezen van telegrammen, gegevens van de MQTT broker en het autorisatie token van Mindergas.nl worden ingesteld.
* **Herstel**: ingevoerde veranderingen die nog niet zijn opgeslagen worden teniet gedaan.
* **Opslaan**: de ingevoerde gegevens worden opgeslagen

### Meterstanden aanpassen

![Edit Maanden tabel](.gitbook/assets/editdata.png)

Het muteren van de maanden tabel is nog niet helemaal zoals het zou moeten zijn. Het is vrij lastig omdat de software zeker moet zijn dat de _jaar/maand_ gegevens, van boven naar beneden, _aflopen en aansluiten_ en ook de meterstanden moeten _een steeds lagere waarde_ hebben. Wordt niet aan voorgaande inter-validatie voldaan, dan kleurt het vakje waar de fout is ontdekt rood en worden de gegevens **niet** opgeslagen. 

{% hint style="success" %}
Klik na iedere verandering op **`[Opslaan]`** \(of in ieder geval toch zo vaak mogelijk!
{% endhint %}

{% hint style="warning" %}
Sommige browser vertalen decimale punten in komma's! Dit is erg verwarrend want de vertaling terug doen ze dan weer niet. Bij het invullen/veranderen van de meterstanden moet een decimale punt \("**.**"\) gebruikt worden, anders wordt de invoer als ongeldig aangemerkt en niet opgeslagen!
{% endhint %}

### Settings aanpassen

![](.gitbook/assets/settings%20%281%29.png)



#### Hostname

De default Hostname is DSMR-API. De documentatie gaat ook uit van deze default hostname. Mocht je de hostname hier veranderen dan moet je bij het lezen van de documentatie overal "_**DSMR-API**_" vervangen door de hier ingevoerde hostname \(in bovenstaand plaatje is de hostname veranderd in "_**DSMR-TST3**_"\).

#### Use Pré DSMR 40 \(0=No, 1=Yes\)

Zet deze rubriek op "1" als je een DSMR 2+ of DSMR 3+ Slimme Meter hebt.  
Deze instelling wordt pas actief nadat de DSMR-logger opnieuw is opgestart.

#### MBus-1 \(2,3,4\) Type Meter

Voer hier het **`Type`** in van de meter die op de betreffende MBus is aangesloten. Het **`Type`** van Gas meters is "_**003**_". Als in jouw installatie de Gas meter is aangesloten op MBus-ID2 voer je bij de rubriek**`"MBus-2 Type meter"`**een "**3**" in. Bij MBus-ID's waar niets op is aangesloten voer je het beste een "0" in.

#### SM Has Fase Info \(0=No, 1=Yes\)

Voer een **1** in als de aangesloten Slimme Meter wél fase informatie afgeeft, voer anders een **0** \(nul\) in. Of jouw Slimme Meter Fase Informatie af geeft kun je zien door naar een telegram te kijken. Geeft jouw Slimme Meter Fase Informatie dan zie je rubrieken met een naam waar `_l1`_,_ `_l2` en `_l3` achter staat. Je hebt een Slimme meter die géén fase info afgeeft als de grafieken leeg blijven.

#### Telegram Lees Interval

Default interval is 10. Dit betekent dat er iedere tien seconden een telegram wordt gelezen en verwerkt. De minimum waarde is 2 seconden.

#### Te gebruiken index.html pagina

De standaard index pagina is "_DSMRindex.html_". Mocht je zelf een GUI schrijven dan kun je hier de naam van de index pagina van jouw GUI invullen \(nadat je jouw **`.html`** pagina naar het bestand systeem hebt ge-upload\).   
Standaard staat er ook een **DSMRindexEDGE.html** pagina op het bestand systeem. Deze is gelijk aan de _DSMRindex.html_ pagina maar hij haalt de _javascript_ en _css_ bestanden uit de github repository zodat aanpassingen \(uitbreidingen of verbeteringen\) automatisch door de DSMR-logger gebruikt worden.   
Het **ADJindex.html** bestand is een bootstrap naar de door [Arjen de Jong](https://github.com/arjendejong12/DSMRloggerGUI) gemaakte GUI, het **HJMindex.html** bestand is een bootstrap naar de door _Erik_ ontwikkelde GUI.   
Je kunt deze GUI's eenvoudig uitproberen door in de FSmanager op deze bestanden te klikken. 

{% hint style="warning" %}
Een nieuw ingevoerde index pagina wordt pas actief na het opnieuw opstarten van de DSMR-logger \(\[ReBoot\] knop in de FSmanager\).
{% endhint %}

#### OLED type

Hier kun je invoeren óf en wat voor OLED schermpje op de DSMR-logger is aangesloten.

* Voer een **0** \(nul\) in als er geen OLED scherm is aangesloten
* Voer een **1** in als het scherm van het type **SDD1306** is
* Voer een **2** in als het scherm van het type **SH1106** is

#### Flip Oled scherm

* Voer **0** \(nul\) in om het scherm standaard te gebruiken
* Voet 1 in als je het scherm "_op zijn kop_" gebruikt.

#### MQTT Top Topic

Dit is het topic waarmee de MQTT berichten naar de broker worden verstuurd. Standaard is het Top Topic "_**DSMR-API**_". In bovenstaand plaatje is het Top Topic veranderd in "_**DSMR-TST3**_".

#### Verzend MQTT berichten

Hier kun je opgeven hoe vaak de DSMR-logger een bericht naar de MQTT broker moet sturen. Voer je hier '0' \(nul\) in dan worden er géén berichten naar de MQTT broker verstuurd. Een waarde kleiner dan de _Telegram Lees Interval_ zorgt ervoor dat na ieder gelezen telegram een bericht naar de MQTT broker wordt verstuurd.

![](.gitbook/assets/dsmr_gui_maanden_kosten.png)

