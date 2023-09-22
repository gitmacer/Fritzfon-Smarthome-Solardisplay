![Demo](https://github.com/gitmacer/Fritzfon-Solardisplay/raw/main/Demo-Images/Demo.jpg)
# Examples/Beispiele:
![SolarDisplay Battery](https://github.com/gitmacer/Fritzfon-Smarthome-Solardisplay/assets/37345589/fce7350f-7f46-4603-8784-0f61328b2df2)
![Solar+ToHouse+House+FromToGrid-Today](https://github.com/gitmacer/Fritzfon-Smarthome-Solardisplay/assets/37345589/2d71dd87-4ab7-41e0-8c07-4111b19c373e)
![Temperatur](https://github.com/gitmacer/Fritzfon-Smarthome-Solardisplay/assets/37345589/f207cb81-e4a4-4f2d-bf21-44c4c890f47a)

[Deutsche Anleitung](https://github.com/gitmacer/Fritzfon-Solardisplay#anleitung)   
[English Guide](https://github.com/gitmacer/Fritzfon-Solardisplay#guide)

# Donationware:   
Beachte, dass ein selbstgewählter Geldbetrag für die Nutzung erwartet wird.   
Bereits 1€ macht einen großen unterschied und sollte jeder ausgeben können.   
Bei Problemen bitte ein Github-Issue erstellen und bei gefallen ein Github Stern vergeben.   

A small donation is gladly received and expected. Nothing against trying out first.   
I am already glad to receive as low as 1€.   
If you experience problems or need help feelfree to create a Github issue.   
Also if you like my Projekt please give it a Github-star.   
www.paypal.me/TimOberle


# Solar image vs smart-home image:   
Solar:
- Nur Solar anzeige kann gewählt werden   
![Solar-Power](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/9f91daf3-7c41-4d00-b749-84b94d2290a1)
- Solar zu Haus Anzeige   
![SolarToHouse Marked](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/ee503f7c-7d6a-434d-b161-d5f1fe88661e)
- Zu Haus und Haus berechnung
- Kwh zu € berechnung

Smart-home image:
- Mehr und freie icon auswahl
- Freie Zeilen möglich
- Beschriftung/Überschrift für jede Zeile
- 3 Zeilen pro icon wenn Wert und Einheit auf klein gesetzt ist   
- Einheit pro Wert   
![Smat-home demo](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/c25822db-7d0e-4c7b-8c77-589de90fc3eb)
- Bunte Kreise   
![circle](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/c1300398-43e4-4751-a4a0-1c1009513d40)

# Eingangs Variabeln
## Solar image:   
| Var-Name              | Beschreibung                              | Datentyp                                                        | Info                                        |
| --------------------- | ----------------------------------------- | --------------------------------------------------------------- | ------------------------------------------- |
| msg.info              | Obere Leiste                              | String                                                          | Wenn nicht gesetzt Datum/Uhr wird angezeigt |
| msg.house             | Haus                                      | String oder Number<br>Number für alle Funktionen wie umrechnen  | Wenn nicht gesetzt wird errechnet           |
| msg.toHouse           | Solar zu Haus                             | String oder Number<br>Number für alle Funktionen wie umrechnen  | Wenn nicht gesetzt wird errechnet           |
| msg.solar             | Solar                                     | String oder Number<br>Number für alle Funktionen wie umrechnen  |                                             |
| msg.solarPercent      | Solar-Prozent                             | String oder Number<br>Number für alle Funktionen wie umrechnen  | Wenn nicht gesetzt wird errechnet           |
| msg.fromGrid          | Vom Stromnetz                             | String oder Number<br>Number für alle Funktionen wie umrechnen  |                                             |
| msg.toGrid            | Zum Stromnetz                             | String oder Number<br>Number für alle Funktionen wie umrechnen  |                                             |
| msg.car               | Zum Auto                                  | String oder Number<br>Number für alle Funktionen wie umrechnen  |                                             |
| msg.carPercent        | Auto-Prozent                              | String oder Number<br>Number für alle Funktionen wie umrechnen  |                                             |
| msg.heatPump          | Zur Wärmepumpe                            | String oder Number<br>Number für alle Funktionen wie umrechnen  |                                             |
| msg.fromBattery       | Von der Batterie                          | String oder Number<br>Number für alle Funktionen wie umrechnen  |                                             |
| msg.toBattery         | Zu der Batterie                           | String oder Number<br>Number für alle Funktionen wie umrechnen  |                                             |
| msg.batteryPercent    | Batterie-Prozent                          | String oder Number<br>Number für alle Funktionen wie umrechnen  |                                             |
| msg.(var name)Unit    | In-Einheit                                | String: "", W, kW, Wmin, Wh, kWh, MWh, € oder T€                | Beispiel: msg.houseUnit = "kWh"             |
| msg.(var name)OutUnit | Out-Einheit                               | String: "", W, kW, kWh, MWh, € oder T€                          | Beispiel: msg.houseOutUnit = "kWh"          |
| msg.solarMax          | Max-Wert um msg.solarPercent auszurechnen | Number (Einheit W)                                              |                                             |
| msg.label             | Beschriftung                              | String                                                          |                                             |

 ## Smart-home image:   
 1. X=Icon Nummer   
 2. X=Zeilen Nummer

| Var-Name             | Beschreibung                                              | Datentyp                                                          | Info                                        |
| -------------------- | --------------------------------------------------------- | ----------------------------------------------------------------- | ------------------------------------------- |
| msg.info             | Obere Leiste                                              | String                                                            | Wenn nicht gesetzt Datum/Uhr wird angezeigt |
| msg.valueXX          | Wert                                                      | String oder Number<br>Number für alle Funktionen wie umrechnen    |                                             |
| msg.negativeValueXX  | Wird abgezogen nutzlich wenn z.B. Netz zu/aus getrennt ist | Number                                                            |                                             |
| msg.unitXX           | Einheit                                                   | String: "", W, kW, Wmin, Wh, kWh, MWh, €, T€, 0-1%, °C, °F oder K | Beispiel: msg.unit11 = "kWh"                |
| msg.outUnitXX        | Anzeige-Einheit                                           | String: "", W, kW, kWh, MWh, €, T€, %, °C, °F oder K              | Beispiel: msg.outUnit11 = "kWh"             |
| msg.labelX           | Beschriftung                                              | String                                                            | Beispiel: msg.label1 = "TV"                 |
| msg.headlineX        | Überschrift                                               | String                                                            | Beispiel: msg.headline2 = "Steckdosen"      |
| msg.circleX          | Bunter-Kreis                                              | String: blue, green, grey, orange, red, white oder yellow         | Beispiel: msg.circle1 = "green"             |
| msg.miniIconX        | Mini-Icon                                                 | String: battery, batteryX, batteryFlash, happy, sceptic, sad, warn, signal, signalNoConnection oder signal0 bis signal4 | |
| msg.miniIconXPercent | Batterie/Signal Prozent                                   | Number: 0-100                                                     |                                             |
| msg.miniIconXDBm     | Signalstärke                                              | Number: -100-0                                                    |                                             |
| msg.miniIconXColor   | Batterie Farbe                                            | String: red, orange, yellow, greenYellow oder green               |                                             |
| msg.roundModeXX      | Rundungsmodus                                             | String: "", Round oder To fixed                                   |                                             |
| msg.decimalsXX       | Kommastellen                                              | Number: -1-∞                                                      | -1 für Standart                             |
| msg.customIconX      | Eigenes Icon                                              | String file path, URL or base64 string                            |                                             |
| msg.customIcon       | If msg.customIconX isn't provided                         | String file path, URL or base64 string                            |                                             |
[Bild zu Base64 string umwandler](https://base64.guru/converter/encode/file)


# Anleitung:
Es sind viele Anleitungen zur Inbetriebnahme von Node-Red verfügbar daher wird dieser Schritt übersprungen.

Installiere [Node-Red image tools](https://flows.nodered.org/node/node-red-contrib-image-tools).   
![Jimp installation](https://user-images.githubusercontent.com/37345589/228313961-9bf6407b-8946-4bc2-8907-313227f4a952.gif)

Lade die neuste Version [hier](https://github.com/gitmacer/Fritzfon-Solardisplay/releases) herunter und importiere diese (solar und/oder Smarthome image).   
![2  import](https://user-images.githubusercontent.com/37345589/228585979-1c44dbf8-88cb-423e-a701-2452e1fb4e81.gif)

Füge ein "http in" node hinzu und vergebe eine Adresse.   
![3  SolarPower](https://user-images.githubusercontent.com/37345589/228586648-7bfe8aad-392e-4944-a9c8-b1b907f3c9d0.gif)

# Daten Quellen:
[Fritz Dect 200/210](https://github.com/gitmacer/Fritzfon-Solardisplay/tree/main#fritzdect-200210)   
[InfluxDB](https://github.com/gitmacer/Fritzfon-Solardisplay/tree/main#influxdb)   

# Fritz!Dect 200/210:   
Füge unter System/FRITZ!Box-Benutzer über die Fritzbox Oberfläche ein neuen benutzer hinzu mit nur SmartHome rechten.   
Melde die Steckdose an der Fritzbox an wenn noch nicht geschehen.   
Notiere die ain ohne leerzeichen unter Smart Home/Geräte und Gruppen/Stift oder vom Gerätegehäuse.   
Installiere "node-red-contrib-fritzapi" über Palette wie du die image-tools installiert hast.   
Füge ein change node hinzu und setze ain auf die notierte nummer.   
![Add Fritz ain change](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/ac329e2b-1d08-44e3-b3a8-393acd6b034a)   

### Solar image:   
Füge ein outlet node hinzu und setze die Zugangsdaten und Action auf "get power".
![Add Fritz outlet](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/ab8ac073-1f4a-471e-aece-e29aa4c1e0c3)   
Füge ein change node hinzu welches msg.solar auf msg.payload setzt.   
![Add payload to solar](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/f40010ac-787c-4377-9d56-bd18b15d37d9)   
Füge ein solar image node hinzu und konfiguriere ihn nach deinen Wünschen.   
![Add solar node](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/5f0320f6-43e0-490e-befa-ea7d05fc58c4)   

### smart-home:   
Importiere folgenden Subflow und setze die Zugangsdaten.   
```
[{"id":"3f152da42a676d42","type":"subflow","name":"Dect 200/210","info":"# override options\r\nmsg.ain as string","category":"","in":[{"x":60,"y":40,"wires":[{"id":"d77040f4713bfce5"}]}],"out":[{"x":1940,"y":40,"wires":[{"id":"99465cf54a644259","port":0}]}],"env":[{"name":"ain","type":"str","value":"","ui":{"type":"input","opts":{"types":["str"]}}}],"meta":{"version":"0.0.2","author":"Tim Oberle","keywords":"fritz"},"color":"#2E90DD","icon":"node-red-contrib-fritzapi/fritz.png"},{"id":"1f0a79874e2a8d70","type":"fritz-outlet","z":"3f152da42a676d42","connection":"4064abf62c97a123","name":"online","action":"getSwitchPresence","x":290,"y":40,"wires":[["853c5c722062d483"]]},{"id":"853c5c722062d483","type":"function","z":"3f152da42a676d42","name":"msg.online","func":"msg.online = msg.payload == 1\nreturn msg;","outputs":1,"noerr":0,"initialize":"","finalize":"","libs":[],"x":430,"y":40,"wires":[["a17d2148153105fe"]]},{"id":"a17d2148153105fe","type":"fritz-outlet","z":"3f152da42a676d42","connection":"4064abf62c97a123","name":"state","action":"getSwitchState","x":570,"y":40,"wires":[["016ff3e84df1a818"]]},{"id":"016ff3e84df1a818","type":"function","z":"3f152da42a676d42","name":"msg.state","func":"msg.state = msg.payload == 1\nreturn msg;","outputs":1,"noerr":0,"initialize":"","finalize":"","libs":[],"x":700,"y":40,"wires":[["268c337afbfc4e5d"]]},{"id":"268c337afbfc4e5d","type":"function","z":"3f152da42a676d42","name":"circle","func":"msg.circle = msg.state ? \"green\" : \"red\";\n\nif(msg.online == true){}\nelse{\n    delete msg.circle;\n}\nreturn msg;","outputs":1,"noerr":0,"initialize":"","finalize":"","libs":[],"x":830,"y":40,"wires":[["60fb6b3b6514189c"]]},{"id":"60fb6b3b6514189c","type":"fritz-outlet","z":"3f152da42a676d42","connection":"4064abf62c97a123","name":"power","action":"getSwitchPower","x":950,"y":40,"wires":[["a86270d47a8a3c11"]]},{"id":"a86270d47a8a3c11","type":"function","z":"3f152da42a676d42","name":"msg.power","func":"msg.power = msg.payload;\nreturn msg;","outputs":1,"noerr":0,"initialize":"","finalize":"","libs":[],"x":1090,"y":40,"wires":[["3a61caa56fda9e4e"]]},{"id":"3a61caa56fda9e4e","type":"fritz-outlet","z":"3f152da42a676d42","connection":"4064abf62c97a123","name":"energy","action":"getSwitchEnergy","x":1240,"y":40,"wires":[["8df7066bef1ab277"]]},{"id":"8df7066bef1ab277","type":"function","z":"3f152da42a676d42","name":"msg.energy","func":"msg.energy = msg.payload;\nreturn msg;","outputs":1,"noerr":0,"initialize":"","finalize":"","libs":[],"x":1390,"y":40,"wires":[["a45259d717a93231"]]},{"id":"a45259d717a93231","type":"fritz-outlet","z":"3f152da42a676d42","connection":"4064abf62c97a123","name":"temp","action":"getTemperature","x":1530,"y":40,"wires":[["d744c1e9f07ca30d"]]},{"id":"d744c1e9f07ca30d","type":"function","z":"3f152da42a676d42","name":"msg.temperature","func":"msg.temperature = msg.payload;\nreturn msg;","outputs":1,"noerr":0,"initialize":"","finalize":"","libs":[],"x":1690,"y":40,"wires":[["99465cf54a644259"]]},{"id":"d77040f4713bfce5","type":"function","z":"3f152da42a676d42","name":"env ain","func":"if (msg.ain === undefined){\n    msg.ain = env.get(\"ain\");\n}\nreturn msg;","outputs":1,"noerr":0,"initialize":"","finalize":"","libs":[],"x":160,"y":40,"wires":[["1f0a79874e2a8d70"]]},{"id":"99465cf54a644259","type":"change","z":"3f152da42a676d42","name":"delete","rules":[{"t":"delete","p":"iconNumber","pt":"msg"},{"t":"delete","p":"payload","pt":"msg"}],"action":"","property":"","from":"","to":"","reg":false,"x":1850,"y":40,"wires":[[]]},{"id":"4064abf62c97a123","type":"fritz-api","name":"","host":"http://fritz.box","strictSSL":true}]
```
![smarthome fritz subflow](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/b3b1f8e0-4c25-4fe1-9a58-03130a8bfdc6)   
Füge ein change node hinzu welches die Werte auf die richtige icon nummer Variable setzt.   
![grafik](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/481df9a3-da3a-4158-8385-05ad69ea7507)   
Füge ein smart-home image node ein und konfiguriere ihn.
![smarthome image](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/d3edddd9-fde1-48b4-a6c8-c6106bc4d5b8)   

[Nächster Schritt: Fritzfon Einstellungen](https://github.com/gitmacer/Fritzfon-Solardisplay#fritzfon)

# InfluxDB:
Installiere InfluxDB nodes.   
![4  influxdb installation](https://user-images.githubusercontent.com/37345589/228587498-278a7f3d-b5b7-4b83-9a84-1a09f5d58356.gif)

Füge ein "influxdb in" node hinzu.   
![5  influxdb](https://user-images.githubusercontent.com/37345589/228587816-514134f8-7eae-494d-a043-812b902ed145.png)

Setze Server und Querry.   
Beispiel query:   
Influxdb 1.X (InfluxQL):
```
SELECT last(*) FROM "Measurement";
```
"*" für alle gespeicherten Variablen.   

Influxdb 2.X (flux):
```
from(bucket: "bucket")
    |> range(start: -1d)
    |> filter(fn: (r) => r._measurement == "Measurement")
    |> last()
```

![6  influxdb](https://user-images.githubusercontent.com/37345589/228588128-2f0f2d29-5f13-400f-81e7-aa7a94a745d8.png)   

Füge ein "change" node hinzu um die daten auf die richtige Variable zu setzen.   
Ich empfehle mithilfe eines Debug-Nodes die richtige Pfad herauszufinden.   
![Debug Pfad](https://github.com/gitmacer/Fritzfon-Smarthome-Solardisplay/assets/37345589/49a6721b-167b-4103-a7ce-89c2e25efcd4)   

z.B. msg.value11 auf   
Influxdb 1.X: `msg.payload[0].last_value`    
Influxdb 2.X: `msg.payload[0]._value`    

![7  change node](https://user-images.githubusercontent.com/37345589/228590676-cb486b06-5e68-40da-a6bc-a8a43e861fc6.png)

Wiederhole die letzten 2 Schritte für alle Daten die angezeigt werden sollen. Dann füge ein "Fritzfon solarimage" node hinzu.   

![8  solarimage node](https://user-images.githubusercontent.com/37345589/228594482-f4ac8136-0f84-418c-950c-0cebd79e1e6b.png)

Bearbeite den "Fritzfon solarimage" node entsprechend was angezeigt werden soll.   
In diesem fall "unit" auf "W"... anschließend wird der Flow übernommen.   

# Fritzfon
Navigiere in der Fritzbox Oberfläche (fritz.box) zu "Telefonie"/Telefoniegeräte/Live-Bilder"   
und klicke auf "Neues Live-Bild hinzufügen"   
Vergebe einen Namen, Adresse (Hostname oder feste IP des Node-red Servers vor der vorhervergebenen Adresse) und setze den Abrufintervall auf z.B. 1 Sec.
![Screenshot 2023-03-29 180119](https://user-images.githubusercontent.com/37345589/228598469-35785386-3213-4023-b37c-20af269b8c4d.png)

Nachdem Bestätigen ist das Display unter "Menu/Heimnetz/Live-Bild" auf dem Fritzfon aufrufbar.   
Tipp: Du kannst Live-Bilder zu den Fritzfon Favoriten hinzufügen für schnelleren Zugriff.   

# Donationware:
Beachte, dass ein selbstgewählter Geldbetrag für die Nutzung erwartet wird.   
www.paypal.me/TimOberle

# Guide:
There are many guids how to install Node-Red available so this step is skipped here.   

You need to install
[Node-Red image tools](https://flows.nodered.org/node/node-red-contrib-image-tools) before importing my subflow.   
![Jimp installation](https://user-images.githubusercontent.com/37345589/228313961-9bf6407b-8946-4bc2-8907-313227f4a952.gif)

Import the latest version from [Releases](https://github.com/gitmacer/Fritzfon-Solardisplay/releases).   
![2  import](https://user-images.githubusercontent.com/37345589/228585979-1c44dbf8-88cb-423e-a701-2452e1fb4e81.gif)

Add a "http in" node and give it a unique url.   
![3  SolarPower](https://user-images.githubusercontent.com/37345589/228586648-7bfe8aad-392e-4944-a9c8-b1b907f3c9d0.gif)

# Get data from InfluxDB:
Install InfluxDB nodes.   
![4  influxdb installation](https://user-images.githubusercontent.com/37345589/228587498-278a7f3d-b5b7-4b83-9a84-1a09f5d58356.gif)

Add a "influxdb in" node.   
![5  influxdb](https://user-images.githubusercontent.com/37345589/228587816-514134f8-7eae-494d-a043-812b902ed145.png)

Configure Server and querry.   
Example querry: 
Influxdb 1.X (InfluxQL):
```
SELECT last(*) FROM "Measurement";
```
"*" for all field keys.   

Influxdb 2.X (flux):
```
from(bucket: "bucket")
    |> range(start: -1d)
    |> filter(fn: (r) => r._measurement == "Measurement")
    |> last()
```

![6  influxdb](https://user-images.githubusercontent.com/37345589/228588128-2f0f2d29-5f13-400f-81e7-aa7a94a745d8.png)

Add a "change" node to set the queried data to right variable.   
I recommend to use a debug node to find the right path.
![Debug Pfad](https://github.com/gitmacer/Fritzfon-Smarthome-Solardisplay/assets/37345589/3014aece-135c-45b0-a749-3a30585643d4)

Influxdb 1.X: `msg.payload[0].last_value`   
Influxdb 2.X: `msg.payload[0]._value`   

# Solar image vs smart-home image:   
Solar:
- Solar only is available   
![Solar-Power](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/9f91daf3-7c41-4d00-b749-84b94d2290a1)
- Solar to home available   
![SolarToHouse Marked](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/ee503f7c-7d6a-434d-b161-d5f1fe88661e)
- To home and home calculation
- Kwh to € calculation

Smart-home image:
- bigger and freely selectable icons   
- Empty Rows possible   
- label/headline for each icon   
- 3 rows per icon if small value and unit is selected
- unit per value   
![Smat-home demo en](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/89de392b-c63c-4eef-9179-69108929e395)
- colored circles   
![circle](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/c1300398-43e4-4751-a4a0-1c1009513d40)

# Input variables
## Solar image:   
| Var-name              | Description                             | Data-type                                                      | Info                                        |
| --------------------- | --------------------------------------- | -------------------------------------------------------------- | ------------------------------------------- |
| msg.info              | Top bar                                 | String                                                         | If not provided date and time will be shown |
| msg.house             | house                                   | String oder Number<br>Number for all features like converting  | If not provided will get calculated         |
| msg.toHouse           | Solar to House                          | String oder Number<br>Number for all features like converting  | If not provided will get calculated         |
| msg.solar             | Solar                                   | String oder Number<br>Number for all features like converting  |                                             |
| msg.solarPercent      | Solar percent                           | String oder Number<br>Number for all features like converting  | If not provided will get calculated         |
| msg.fromGrid          | From grid                               | String oder Number<br>Number for all features like converting  |                                             |
| msg.toGrid            | To grid                                 | String oder Number<br>Number for all features like converting  |                                             |
| msg.car               | To car                                  | String oder Number<br>Number for all features like converting  |                                             |
| msg.carPercent        | Car percent                             | String oder Number<br>Number for all features like converting  |                                             |
| msg.heatPump          | To heatpump                             | String oder Number<br>Number for all features like converting  |                                             |
| msg.fromBattery       | From battery                            | String oder Number<br>Number for all features like converting  |                                             |
| msg.toBattery         | To battery                              | String oder Number<br>Number for all features like converting  |                                             |
| msg.batteryPercent    | Battery percent                         | String oder Number<br>Number for all features like converting  |                                             |
| msg.(var name)Unit    | Input-Unit                              | String: "", W, kW, Wmin, Wh, kWh, MWh, € r T€                  | Example: msg.houseUnit = "kWh"              |
| msg.(var name)OutUnit | Shown-Unit                              | String: "", W, kW, kWh, MWh, € or T€                           | Example: msg.houseOutUnit = "kWh"           |
| msg.solarMax          | Max Value to calculate msg.solarPercent | Number (Unit W)                                                |                                             |
| msg.label             | Label                                   | String                                                         |                                             |

 ## Smart-home image:   
| Var-name             | Description                                               | Data-type                                                         | Info                                        |
| -------------------- | --------------------------------------------------------- | ----------------------------------------------------------------- | ------------------------------------------- |
| msg.info             | Top bar                                                   | String                                                            | If not provided date and time will be shown |
| msg.valueXX          | Value<br>1. X=icon number<br>2. X=row nummer              | String or Number<br>Number for all features like converting       |                                             |
| msg.unitXX           | Input unit<br>1. X=icon number<br>2. X=row number         | String: "", W, kW, Wmin, Wh, kWh, MWh, €, T€, 0-1%, °C, °F or K   | Example: msg.unit11 = "kWh"                |
| msg.outUnitXX        | Shown unit<br>1. X=icon number<br>2. X=row number         | String: "", W, kW, kWh, MWh, €, T€, %, °C, °F or K                | Example: msg.outUnit11 = "kWh"             |
| msg.labelX           | Label<br>X=icon number                                    | String                                                            | Example: msg.label1 = "TV"                 |
| msg.headlineX        | Headline<br>X=icon number                                 | String                                                            | Example: msg.headline2 = "Steckdosen"      |
| msg.circleX          | colored-circle<br>X=icon number                           | String: blue, green, grey, orange, red, white oder yellow         | Example: msg.circle1 = "green"             |
| msg.miniIconX        | mini icon<br>X=icon number                                | String: battery, batteryX, batteryFlash, happy, sceptic, sad, warn, signal, signalNoConnection or signal0 to signal4 | |
| msg.miniIconXPercent | Battery and signal percent                                | Number: 0-100                                                     |                                             |
| msg.miniIconXDBm     | signal strength                                           | Number: -100-0                                                    |                                             |
| msg.miniIconXColor   | Batterie Farbe                                            | String: red, orange, yellow, greenYellow or green                 |                                             |
| msg.roundModeXX      | Rounding mode<br>1. X=icon number<br>2. X=row number      | String: "", Round oder To fixed                                   |                                             |
| msg.decimalsXX       | Decimals<br>1. X=icon number<br>2. X=row number           | Number: -1-∞                                                      | -1 for standard                             |

![7  change node](https://user-images.githubusercontent.com/37345589/228590676-cb486b06-5e68-40da-a6bc-a8a43e861fc6.png)

Repeat last 2 steps for all data you want to show. Then add the imported "Fritzfon solarimage".

![8  solarimage node](https://user-images.githubusercontent.com/37345589/228594482-f4ac8136-0f84-418c-950c-0cebd79e1e6b.png)

Edit "Fritzfon solarimage". In this case for example change the "unit" to "W" and Round mode to "To fixed".   
Then deploy the flow.   

# Config fritzfon
Navigate to "Telephony"/Telephony Devices/Live Image"   
and click on "Add New Live Image"   
Set a unique name, url you chosed before (Add hostname or fixed IP of the Node-Red server in front) and set intervall to 1 sec.
![Screenshot 2023-03-29 180119](https://user-images.githubusercontent.com/37345589/228598469-35785386-3213-4023-b37c-20af269b8c4d.png)

After applying you should be able to show the image on your Fritzfon under "Menu/Home Network/Live Image".
Tipp: you can add Live-Bild to favourites  for faster access.

# Donationware:
Feel free to try my Project first and decide how much it is worths to you afterwards.   
www.paypal.me/TimOberle
