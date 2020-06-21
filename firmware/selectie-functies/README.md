# Selecteren compiler opties

### Overzicht te selecteren functies <a id="overzicht-te-selecteren-functies"></a>

Tijdens het compileren van de firmware kun je bepaalde functionaliteit in- en uit-schakelen door de \#defines wél of níet door twee slashes \("//"\) vooraf te laten gaan.

In onderstaande tabel kun je zien of een bepaalde functionaliteit beschikbaar is voor de verschillende versies van de DSMR-logger.

<table>
  <thead>
    <tr>
      <th style="text-align:left">#define</th>
      <th style="text-align:left">Functie</th>
      <th style="text-align:left">Optioneel</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><a href="define-is_esp12.md">USE_REQUEST_PIN</a>
      </td>
      <td style="text-align:left">Geeft aan of je de firmware voor een ESP12 of andere (ESP-01) processor
        compileren</td>
      <td style="text-align:left">
        <p>Voor v4.0 en hoger: NEE</p>
        <p>Voor andere versies: JA</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="define-use_update_server.md">USE_UPDATE_SERVER</a>
      </td>
      <td style="text-align:left">Met de Update Server kun je vanuit de FSexplorer updates van de firmware
        installeren</td>
      <td style="text-align:left">JA</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="define-use_belgium_protocol.md">USE_BELGIUM_PROTOCOL</a>
      </td>
      <td style="text-align:left">Voor Belgische Slimme Meters</td>
      <td style="text-align:left">
        <p>JA</p>
        <p>niet in combinatie met USE_PRE40_PROTOCOL</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="define-use_pre40_protocol.md">USE_PRE40_PROTOCOL</a>
      </td>
      <td style="text-align:left">Voor &quot;oude&quot; Slimme Meters</td>
      <td style="text-align:left">
        <p>JA</p>
        <p>niet in combinatie met USE_BELGIUM_PROTOCOL</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="define-use_ntp_time.md">USE_NTP_TIME</a>
      </td>
      <td style="text-align:left">Gebruik de tijd van een NTP server i.p.v. die van de Slimme Meter</td>
      <td
      style="text-align:left">
        <p>JA</p>
        <p>alleen in combinatie met USE_PRE40_PROTOCOL</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="define-use_mqtt.md">USE_MQTT</a>
      </td>
      <td style="text-align:left">Deze optie zorgt ervoor dat de functionaliteit voor het versturen van
        gegevens naar een MQTT broker wordt ingebouwd</td>
      <td style="text-align:left">JA</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="define-use_mindergas.md">USE_MINDERGAS</a>
      </td>
      <td style="text-align:left">Deze optie zorgt ervoor dat de functionaliteit voor het versturen van
        gegevens naar <a href="https://mindergas.nl/">mindergas.nl</a> waar je huidige
        gasverbruik kunt vergelijken met anderen.</td>
      <td style="text-align:left">JA</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="use_syslogger.md">USE_SYSLOGGER</a>
      </td>
      <td style="text-align:left">Met de System logger is het mogelijk om debug informatie over de werking
        van de DSMR-logger op te slaan in een bestand van 500 regels.</td>
      <td style="text-align:left">
        <p>JA</p>
        <p>alleen gebruiken om te debuggen.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="define-show_passwrds.md">SHOW_PASSWORDS</a>
      </td>
      <td style="text-align:left">Of je de gebruikte passwords in het Systeem Info scherm en via telnet
        wilt tonen</td>
      <td style="text-align:left">JA</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="define-has_no_meter.md">HAS_NO_METER</a>
      </td>
      <td style="text-align:left">Als je geen Slimme Meter op de DSMR-logger hebt aangesloten</td>
      <td style="text-align:left">
        <p>JA</p>
        <p>alleen om te testen</p>
      </td>
    </tr>
  </tbody>
</table>

```text

/******************** compiler options  ********************************************/
#define IS_ESP12                  // define if it's a 'bare' ESP-12 (no reset/flash functionality on board)
#define USE_UPDATE_SERVER         // define if there is enough memory and updateServer to be used
//  #define USE_BELGIUM_PROTOCOL      // define if Slimme Meter is a Belgium Smart Meter
//  #define USE_PRE40_PROTOCOL        // define if Slimme Meter is pre DSMR 4.0 (2.2 .. 3.0)
//  #define USE_NTP_TIME              // define to generate Timestamp from NTP (Only Winter Time for now)
//  #define HAS_NO_SLIMMEMETER        // define for testing only!
#define USE_MQTT                  // define if you want to use MQTT
#define USE_MINDERGAS             // define if you want to update mindergas (also add token down below)
//  #define USE_SYSLOGGER             // define if you want to use the sysLog library for debugging
//  #define SHOW_PASSWRDS             // well .. show the PSK key and MQTT password, what else?
/******************** don't change anything below this comment **********************/

```

