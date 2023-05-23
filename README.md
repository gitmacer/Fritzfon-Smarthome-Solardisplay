[Deutsche Anleitung](https://github.com/gitmacer/Fritzfon-Solardisplay/edit/main/README.md#anleitung)   
[English Guide](https://github.com/gitmacer/Fritzfon-Solardisplay/blob/main/README.md#guide)

# Donationware: a small donation is gladly received and expected. Nothing against trying out first 
www.paypal.me/TimOberle
# If you experience problems or need help feelfree to create a Github issue.
# Fritzfon-Solardisplay

Show information about your solarsystem and powermeter on your Fritzfons by using the ability to show webcam images and Node-Red.   
![Demo](https://github.com/gitmacer/Fritzfon-Solardisplay/raw/main/Demo-Images/Demo.jpg)

# Anleitung:
Es sind viele Anleitungen zur Inbetriebnahme von Node-Red verfügbar daher wird dieser Schritt übersprungen.

Installiere [Node-Red image tools](https://flows.nodered.org/node/node-red-contrib-image-tools).   
![Jimp installation](https://user-images.githubusercontent.com/37345589/228313961-9bf6407b-8946-4bc2-8907-313227f4a952.gif)

Lade die neuste Version [hier](https://github.com/gitmacer/Fritzfon-Solardisplay/releases) herunter.   
![2  import](https://user-images.githubusercontent.com/37345589/228585979-1c44dbf8-88cb-423e-a701-2452e1fb4e81.gif)

Füge ein "http in" node hinzu und vergebe eine Adresse.   
![3  SolarPower](https://user-images.githubusercontent.com/37345589/228586648-7bfe8aad-392e-4944-a9c8-b1b907f3c9d0.gif)



# Daten von InfluxDB:
Installiere InfluxDB nodes.   
![4  influxdb installation](https://user-images.githubusercontent.com/37345589/228587498-278a7f3d-b5b7-4b83-9a84-1a09f5d58356.gif)

Füge ein "influxdb in" node hinzu.   
![5  influxdb](https://user-images.githubusercontent.com/37345589/228587816-514134f8-7eae-494d-a043-812b902ed145.png)

Setze Server und Querry.   
Beispiel query:   
Influxdb 1.X (InfluxQL):
```
SELECT last("Measurement") FROM "Database";
```
Influxdb 2.X (flux):
```
from(bucket: "bucket")
    |> range(start: -1d)
    |> filter(fn: (r) => r._measurement == "Measurement")
    |> last()
```

![6  influxdb](https://user-images.githubusercontent.com/37345589/228588128-2f0f2d29-5f13-400f-81e7-aa7a94a745d8.png)

Füge ein "change" node hinzu um die daten auf die richtige Variable zu setzen.   
Influxdb 1.X: `msg.payload.0.last`   
Influxdb 2.X: `msg.payload[0]._value`    

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
- Einheit pro Wert   
![Smat-home demo](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/c25822db-7d0e-4c7b-8c77-589de90fc3eb)

# Eingangs Variabeln
Solar image:   
 - msg.info (obere Leiste) (Wenn nicht gesetzt Datum/Uhr wird angezeigt)
 - msg.house (Haus) (Wenn nicht gesetzt wird errechnet)
 - msg.toHouse (Solar zu Haus) (Wenn nicht gesetzt wird errechnet)
 - msg.solar (Solar)
 - msg.solarPercent (Solar-Prozent) (Wenn nicht gesetzt wird errechnet)
 - msg.fromGrid (vom Stromnetz)
 - msg.toGrid (zum Stromnetz)
 - msg.car (zum Auto)
 - msg.carPercent (Auto-Prozent)
 - msg.heatPump (zur Wärmepumpe)
 - msg.fromBattery (von der Batterie)
 - msg.toBattery (zu der Batterie)
 - msg.batteryPercent (Batterie-Prozent)
 
 Smart-home image:   
 - msg.info (Wenn nicht gesetzt Datum/Uhr wird angezeigt)
 - msg.value11   
 - msg.value12   
 - msg.value13   
 - msg.value21   
 - msg.value22   
 - msg.value23   
 - msg.value31   
 - msg.value32   
 - msg.value33  
 - msg.value41   
 - msg.value42   
 - msg.value43   

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
Tipp: Du kannst Live-Bilder zu den Favoriten hinzufügen für schnelleren zugriff.   

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
SELECT last("Measurement") FROM "Database";
```
Influxdb 2.X (flux):
```
from(bucket: "bucket")
    |> range(start: -1d)
    |> filter(fn: (r) => r._measurement == "Measurement")
    |> last()
```

![6  influxdb](https://user-images.githubusercontent.com/37345589/228588128-2f0f2d29-5f13-400f-81e7-aa7a94a745d8.png)

Add a "change" node to set the queried data to one of the following variables.   
Influxdb 1.X: `msg.payload.0.last`   
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
- unit per value   
![Smat-home demo en](https://github.com/gitmacer/Fritzfon-Solardisplay/assets/37345589/89de392b-c63c-4eef-9179-69108929e395)

# Input variables
Solar image:   
 - msg.info (if not provided clock will be shown)
 - msg.house (if not provided will get calculated)
 - msg.toHouse (if not provided will get calculated)
 - msg.solar
 - msg.solarPercent (if not provided will get calculated)
 - msg.fromGrid
 - msg.toGrid
 - msg.car
 - msg.carPercent
 - msg.heatPump
 - msg.fromBattery
 - msg.toBattery
 - msg.batteryPercent
 
Smart-home image:   
 - msg.info (if not provided clock will be shown)
 - msg.value11   
 - msg.value12   
 - msg.value13   
 - msg.value21   
 - msg.value22   
 - msg.value23   
 - msg.value31   
 - msg.value32   
 - msg.value33   
 - msg.value41   
 - msg.value42   
 - msg.value43   

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
