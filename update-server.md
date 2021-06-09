# Update Server

Met de Update Server is het mogelijk om firmware en het SPIFFS naar een DSMR-logger te flashen.

Je kunt de Update Server op twee manieren opstarten:

* Door op de knop \[Update Firmware\] in de FSexplorer te klikken
* Door in de browser de volgende URL in te toetsen:      **http://dsmr-api.local/update** of:      **http://&lt;hetIPadresVanDeDSMRlogger&gt;/update**

![](.gitbook/assets/updateserver.png)

### Flash Firmware

Om \(nieuwe\) firmware te flashen moet je op de knop \[Choose file\] onder de kop "Selecteer een **.ino.bin** bestand" klikken.

![](.gitbook/assets/chooseino.png)

Er verschijnt nu een drop-down window waar je de gewenste firmware kunt selecteren.

![](.gitbook/assets/choose_ino_bin.png)

Klik vervolgens op \[Flash Firmware\]

### Flash File Systeem

Om een nieuw bestands systeem op de DSMR-logger te flashen klik je op de knop \[Choose file\] onder de kop "Selecteer een **.mklittlefs.bin** bestand".

![](.gitbook/assets/choosespiffs.png)

Er verschijnt nu een drop-down window waar je het gewenste xyz.mklittlefs.bin bestand systeem kunt selecteren.

![](.gitbook/assets/choose_spiffs_bin.png)

Klik vervolgens op de knop \[Flash FileSYS\]

### Flashen is geslaagd

![](.gitbook/assets/image.png)

