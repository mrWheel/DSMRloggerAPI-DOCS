# Beschrijving restAPI's

Alle beschikbare gegevens kunnen via restAPI call's bij de DSMR-logger worden opgevraagd. De restAPI's zijn verdeelt in drie groepen. Informatie die met de hardware en firmware te maken heeft \(`/dev`\), informatie die met de Slimme Meter te maken heeft \(`/sm`\) en historische gegevens die, aan de hand van de door de Slimme Meter afgegeven gegevens, door de DSMR-logger in bestanden worden opgeslagen \(`/hist`\).

* [DSMR-logger gerelateerde restAPI's](dsmr-logger-gerelateerde-restapis.md)
* [Slimme Meter gerelateerde restAPI's](slimme-meter-gerelateerde-restapis.md)
* [Historie gerelateerde restAPI's](historische-gegevens-gerelateerde-restapis.md)

## Aanroepen restAPI vanuit verschillende systemen

Een restAPI kan op verschillende manieren worden aangeroepen.

* [Javascript](./#javascript)
* [Unix command](./#unix-command)
* [Home Assistant](./#home-assistant)
* [Arduino met Ethernet Shield](./#arduino-met-ethernet-shield)
* [ESP8266](./#esp8266-wifi)
* [ESP32](./#esp32-wifi)

With some help from random

### Javascript

```text
    fetch("http://dsmr-api.local/api/v1/dev/time")
      .then(response => response.json())
      .then(json => {
        console.log("parsed .., data is ["+ JSON.stringify(json)+"]");
        for( let i in json.devtime ){
            if (json.devtime[i].name == "time")
            {
              console.log("Got new time ["+json.devtime[i].value+"]");
              document.getElementById('theTime').innerHTML = json.devtime[i].value;
            }
          }
      })
      .catch(function(error) {
        var p = document.createElement('p');
        p.appendChild(
          document.createTextNode('Error: ' + error.message)
        );
      });     

```

### Unix command

```text
curl http://dsmr-api.local/api/v1/dev/time
```

Geeft dit als output:

```text
{"devtime":[
   {"name": "time", "value": "2020-03-23 11:45:40"},
   {"name": "epoch", "value": 1584963941}
]}
```

### Home Assistant

configuration.yaml:

```text
### configuration.yaml
### DSMRloggerAPI 
  - platform: rest
    name: "Levering"
    resource: http://<ip-dsmr-logger>/api/v1/sm/fields/power_returned
    unit_of_measurement: "kWh"
    value_template: '{{ value_json.fields[1].value | round(3) }}'

  - platform: rest
    name: "Laatste Update restAPI"
    resource: http://192.168.2.106/api/v1/sm/fields/timestamp
#   value_template: '{{ value_json.fields[0].value }}'
    value_template: >
      {{      value_json.fields[0].value[4:6] + "-" + 
              value_json.fields[0].value[2:4] + "-" + 
         "20"+value_json.fields[0].value[0:2] + "   " + 
              value_json.fields[0].value[6:8] + ":" + 
              value_json.fields[0].value[8:10] + ":" + 
              value_json.fields[0].value[10:13] }}

  - platform: rest
    name: "Levering l1"
    resource: http://192.168.2.106/api/v1/sm/fields/power_returned_l1
    unit_of_measurement: "Watt"
    value_template: '{{ (value_json.fields[1].value | float * 1000.0) | round(1) }}'

  - platform: rest
    name: "Levering l2"
    resource: http://192.168.2.106/api/v1/sm/fields/power_returned_l2
    unit_of_measurement: 'Watt'
    value_template: '{{ (value_json.fields[1].value | float * 1000.0) | round(1) }}'

  - platform: rest
    name: "Levering l3"
    resource: http://192.168.2.106/api/v1/sm/fields/power_returned_l3
    unit_of_measurement: 'Watt'
    value_template: '{{ (value_json.fields[1].value | float * 1000.0) | round(1) }}'

```

geeft dit resultaat:

![](../.gitbook/assets/ha_restapi.png)

{% hint style="warning" %}
Met hassOS lukt het mij niet om bij resource de hostname \(DSMR-API.local\) te gebruiken. Met het IP adres lukt het wel.
{% endhint %}

### Arduino met Ethernet shield

Ik ben ook niet erg handig met JSON libraries \(liefst parse ik de data helemaal zelf zodat ik ook alles zelf "in de hand" heb\). Het zou mij daarom ook niet verbazen als onderstaande code simpeler en beter kan.

Ik heb zelf geen Ethernet Shield dus deze code heb ik niet kunnen testen :-\(

```text
// in the main program:
#include <Ethernet.h>
#include <SPI.h>
#include <Arduino_JSON.h>  // let op! dit is een andere library dan "ArduinoJson"
//
#define _READINTERVAL   60000
//
const char  *serverPath = "http://192.168.1.106/api/v1/sm/actual";
String      dsmrReadings;
uint32_t    lastRead = 0;

//--------------------------------------------------------------------------
String dsmrGETRequest(const char* dsmrLogger) 
{
  EthernetClient DSMRclient;
  DSMRclient.setTimeout(10000);
  String payload = "{}"; 
  int    plIndex = 0;
   
  // Your IP address with path or Domain name with URL path 
  if (DSMRclient.connect(ipDSMR, 80)) 
  {
    Serial.println("connected");
    // Make a HTTP request:
    DSMRclient.println("GET /api/v1/sm/actual HTTP/1.1");
    DSMRclient.println("Host: 192.168.1.106");
    DSMRclient.println("Connection: close");
    DSMRclient.println();
  } 
  else 
  {
    // if you didn't get a connection to the server:
    Serial.println("connection failed");
    return "Error";
     }

  while(DSMRclient.connected()) 
  {
    if(DSMRclient.available())
    {
      // read an incoming byte from the server and print it to serial monitor:
      char c = DSMRclient.read();
      payload[plIndex++] = c;
      payload[plIndex]   = 0;
    }
  }
  // Free resources
  DSMRclient.stop();

  return payload;
  
} // dsmrGETrequestArduino()


//--------------------------------------------------------------------------
void setup()
{
  // setup Serial ..
  .
  .
  // Initialize Ethernet library
  byte mac[] = {0xDE, 0xAD, 0xBE, 0xEF, 0xFE, 0xED};
  byte ipDSMR[]  = { 192, 168, 1, 106 };    // address of the DSMR-logger   
  if (!Ethernet.begin(mac)) 
  {
    Serial.println("Failed to configure Ethernet");
    return;
  }
  delay(1000);
  .
  .
  lastRead = millis() + _READINTERVAL;
  
}  // setup()


```

Verder moet je de [Algemene functies](./#algemene-functies) onderaan deze pagina in je sketch opnemen.

### ESP8266 \(WiFi\)

With some help from [Random Nerd Tutorials](https://randomnerdtutorials.com/esp8266-nodemcu-http-get-post-arduino/)!

Ik ben niet erg handig met JSON libraries \(liefst parse ik de data helemaal zelf zodat ik ook alles zelf "in de hand" heb\). Het zou mij daarom ook niet verbazen als onderstaande code simpeler en beter kan.

```text
// Include in the main program:
#include <WiFi.h>
#include <HTTPClient.h>
#include <Arduino_JSON.h>  // let op! Niet ArduinoJson!
//
#define _READINTERVAL 60000

const char *ssid       = "replaceWithYourSSID";
const char *password   = "replaceWithYourPassword";
const char *serverPath = "http://192.168.1.106/api/v1/sm/actual";
String     dsmrReadings;
uint32_t   lastRead    = 0;

//--------------------------------------------------------------------------
String dsmrGETRequest(const char* dsmrLogger) 
{
  HTTPClient DSMRclient;
    
  // Your IP address with path or Domain name with URL path 
  DSMRclient.begin(dsmrLogger);
  
  // Send HTTP POST request
  int httpResponseCode = DSMRclient.GET();
  
  String payload = "{}"; 
  
  if (httpResponseCode > 0) 
  {
    Serial.print("HTTP Response code: ");
    Serial.println(httpResponseCode);
    payload = DSMRclient.getString();
  }
  else 
  {
    Serial.print("Error code: ");
    Serial.println(httpResponseCode);
    return "Error";
  }
  // Free resources
  DSMRclient.end();

  return payload;
  
} // dsmrGETrequest()


//--------------------------------------------------------------------------
void setup() 
{
  // setup serial ..
  .
  .
  // setup WiFi ..
  WiFi.begin(ssid, password);
  Serial.println("Connecting");
  while(WiFi.status() != WL_CONNECTED) 
  {
    delay(500);
    Serial.print(".");
  }
  Serial.println("");
  Serial.print("Connected to WiFi network with IP Address: ");
  Serial.println(WiFi.localIP());
  
  lastRead = millis() + _READINTERVAL;
  .
  .
    
} // setup()

```

Verder moet je de [Algemene functies](./#algemene-functies) onderaan deze pagina in je sketch opnemen.

### ESP32 \(WiFi\)

With some help from [Random Nerd Tutorials](https://randomnerdtutorials.com/esp32-http-get-open-weather-map-thingspeak-arduino/).

Ik ben niet erg handig met JSON libraries \(liefst parse ik de data helemaal zelf zodat ik ook alles zelf "in de hand" heb\). Het zou mij daarom ook niet verbazen als onderstaande code simpeler en beter kan.

```text
// Include in the main program:
#include <WiFi.h>
#include <HTTPClient.h>
#include <Arduino_JSON.h>  // let op! Niet ArduinoJson!
//
#define _READINTERVAL 60000

const char *ssid       = "replaceWithYourSSID";
const char *password   = "replaceWithYourPassword";
const char *serverPath = "http://192.168.1.106/api/v1/sm/actual";
String     dsmrReadings;
uint32_t   lastRead    = 0;

//--------------------------------------------------------------------------
String dsmrGETRequest(const char* dsmrLogger) 
{
  HTTPClient DSMRclient;
    
  // Your IP address with path or Domain name with URL path 
  DSMRclient.begin(dsmrLogger);
  
  // Send HTTP POST request
  int httpResponseCode = DSMRclient.GET();
  
  String payload = "{}"; 
  
  if (httpResponseCode > 0) 
  {
    Serial.print("HTTP Response code: ");
    Serial.println(httpResponseCode);
    payload = DSMRclient.getString();
  }
  else 
  {
    Serial.print("Error code: ");
    Serial.println(httpResponseCode);
    return "Error";
  }
  // Free resources
  DSMRclient.end();

  return payload;
  
} // dsmrGETrequest()


//--------------------------------------------------------------------------
void setup() 
{
  // setup Serial ..
  .
  .
  // setup WiFi ..
  WiFi.begin(ssid, password);
  Serial.println("Connecting");
  while(WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }
  Serial.println("");
  Serial.print("Connected to WiFi network with IP Address: ");
  Serial.println(WiFi.localIP());
  
  lastRead = millis() + _READINTERVAL;
  .
  .
    
} // setup()

```

Verder moet je de [Algemene functies](./#algemene-functies) onderaan deze pagina in je sketch opnemen.

### Algemene functies

```text
//--------------------------------------------------------------------------
String splitJsonArray(String data, int index)
{
  int found = 0;
  int strIndex[] = {0, -1};
  int maxIndex = data.length()-1;

  for(int i=0; i<=maxIndex && found<=index; i++)
  {
    if((data.charAt(i) == '}' && data.charAt(i+1) == ',') || i==maxIndex)
    {
        found++;
        strIndex[0] = strIndex[1]+1;
        strIndex[1] = (i == maxIndex) ? i+1 : i;
        if (data.charAt(i+1) == ',') data[i+1] = ' ';
    }
  }

  return found>index ? data.substring(strIndex[0], strIndex[1]+1) : "";
  
} // splitJsonArray()


//--------------------------------------------------------------------------
String removeQuotes(JSONVar in)
{
  String in2 = JSON.stringify(in);
  in2.replace("\"", "");
  return in2;
    
} // removeQuotes()


//--------------------------------------------------------------------------
void readDsmrLogger()
{
  dsmrReadings = dsmrGETRequest(serverPath);
  //Serial.println(dsmrReadings);
  JSONVar myObject = JSON.parse(dsmrReadings);
  
  // JSON.typeof(jsonVar) can be used to get the type of the var
  if (JSON.typeof(myObject) == "undefined") {
    Serial.println("Parsing input failed!");
    return;
  }
  // This is how the "actual" JSON object looks like:
  //   {"actual":[
  //       {"name":"timestamp","value":"200911140716S"}
  //      ,{"name":"energy_delivered_tariff1","value":3433.297,"unit":"kWh"}
  //      ,{"name":"energy_delivered_tariff2","value":4453.041,"unit":"kWh"}
  //      ,{"name":"energy_returned_tariff1","value":678.953,"unit":"kWh"}
  //          ...
  //      ,{"name":"power_delivered_l2","value":0.071,"unit":"kW"}
  //      ,{"name":"power_delivered_l3","value":0,"unit":"kW"}
  //      ,{"name":"power_returned_l1","value":0,"unit":"kW"}
  //      ,{"name":"power_returned_l2","value":0,"unit":"kW"}
  //      ,{"name":"power_returned_l3","value":0.722,"unit":"kW"}
  //      ,{"name":"gas_delivered","value":2915.08,"unit":"m3"}
  //    ]}
  String actualData = JSON.stringify(myObject["actual"]);
  actualData.replace("[", "");
  actualData.replace("]", "");

  for(int i = 0; i < 30; i++)
  {
    String field = splitJsonArray(actualData, i);
    if (field.length() > 0)
    {
      Serial.println(field);
      JSONVar nextObject = JSON.parse(field);
      JSONVar dataArray = nextObject.keys();
      //Serial.print("dataArray.length(): ");
      //Serial.println(dataArray.length());
      for (int i = 0; i < dataArray.length(); i++) 
      {
        JSONVar value = nextObject[dataArray[i]];
        Serial.print(removeQuotes(dataArray[i]));
        Serial.print(" \t-> ");
        Serial.println(removeQuotes(value));
      }
    }
  } // loop over all data
      
} // readDsmrLogger()
```

In de main loop\(\) function moet deze code komen:

```text

//--------------------------------------------------------------------------
void loop()
{
  if ((millis() - lastRead) > _READINTERVAL)
  {
    lastRead = millis();
    Serial.println("\r\nread API from DSMR-logger...");
    readDsmrLogger();
    Serial.println("========================================");
  }
  .
  .
}  // loop()
```



### Andere systemen

Veel andere systemen hebben hun eigen manier om restAPI's op te vragen. Lees hiervoor de betreffende documentatie.

