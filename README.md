# Donationware: a small donation is gladly received and expected. Nothing against trying out first 
www.paypal.me/TimOberle
# If you experience problems or need help feelfree to create a Github issue.
# Fritzfon-Solardisplay

This Project uses the ability to show webcam images (Live-Images) on Fritzfons to display information about your solarsystem and powermeter.
All processing is done inside [Node-Red](https://nodered.org/).
![Demo](https://github.com/gitmacer/Fritzfon-Solardisplay/raw/main/Demo-Images/Demo.jpg)

# Anleitung:
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
Example querry: `SELECT last("Measurement") FROM "Database";`

![6  influxdb](https://user-images.githubusercontent.com/37345589/228588128-2f0f2d29-5f13-400f-81e7-aa7a94a745d8.png)

Füge ein "change" node hinzu um die daten auf die richtige Variable zu setzen `msg.payload.0.last`
 - msg.info (Wenn nicht gesetzt Datum/Uhr wird angezeigt)
 - msg.house (Wenn nicht gesetzt wird errechnet)
 - msg.toHouse (Wenn nicht gesetzt wird errechnet)
 - msg.solar
 - msg.solarPercent
 - msg.fromGrid
 - msg.toGrid
 - msg.car
 - msg.carPercent
 - msg.heatPump
 - msg.fromBattery
 - msg.toBattery
 - msg.batteryPercent

![7  change node](https://user-images.githubusercontent.com/37345589/228590676-cb486b06-5e68-40da-a6bc-a8a43e861fc6.png)

Wiederhole die letzten 2 Schritte für alle Daten die angezeigt werden sollen. Dann füge ein "Fritzfon solarimage" node hinzu.   

![8  solarimage node](https://user-images.githubusercontent.com/37345589/228594482-f4ac8136-0f84-418c-950c-0cebd79e1e6b.png)

Bearbeite den "Fritzfon solarimage" node entsprechend was angezeigt werden soll.   
In diesem fall "unit" auf "W"... anschließend wird der Flow übernommen.   

# Fritzfon
Navigiere in der Fritzbox Oberfläche (fritz.box) zu "Telefonie"/Telefoniegeräte/Live-Bilder"   
und klicke auf "Neues Live-Bild hinzufügen"   
Vergebe einen Namen, Adresse (Hostname oder Ip vor der vorhervergebenen Adresse) und setze den Abrufintervall auf z.B. 1 Sec.
![Screenshot 2023-03-29 180119](https://user-images.githubusercontent.com/37345589/228598469-35785386-3213-4023-b37c-20af269b8c4d.png)

Nachdem Bestätigen ist das Display unter "Menu/Heimnetz/Live-Bild" auf dem Fritzfon aufrufbar.   
Tipp: Du kannst Live-Bilder zu den Favoriten hinzufügen für schnelleren zugriff.   

# Donationware:
Beachte, dass ein selbstgewählter Geldbetrag für die Nutzung erwartet wird.   
www.paypal.me/TimOberle

# Guide:
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
Example querry: `SELECT last("Measurement") FROM "Database";`

![6  influxdb](https://user-images.githubusercontent.com/37345589/228588128-2f0f2d29-5f13-400f-81e7-aa7a94a745d8.png)

Add a "change" node to set the queried data to one of the following variables. `msg.payload.0.last`
 - msg.info (if not provided clock will be shown)
 - msg.house (if not provided will get calculated)
 - msg.toHouse (if not provided will get calculated)
 - msg.solar
 - msg.solarPercent
 - msg.fromGrid
 - msg.toGrid
 - msg.car
 - msg.carPercent
 - msg.heatPump
 - msg.fromBattery
 - msg.toBattery
 - msg.batteryPercent

![7  change node](https://user-images.githubusercontent.com/37345589/228590676-cb486b06-5e68-40da-a6bc-a8a43e861fc6.png)

Repeat last 2 steps for all data you want to show. Then add the imported "Fritzfon solarimage".

![8  solarimage node](https://user-images.githubusercontent.com/37345589/228594482-f4ac8136-0f84-418c-950c-0cebd79e1e6b.png)

Edit "Fritzfon solarimage". In this case for example change the "unit" to "W" and Round mode to "To fixed".   
Then deploy the flow.   

# config Fritzfon
Navigate to "Telefonie"/Telefoniegeräte/Live-Bilder"   
and click on "Neues Live-Bild hinzufügen"   
Set a unique name, url you chosed before (Add hostname or ip in front) and set intervall to 1 sec.
![Screenshot 2023-03-29 180119](https://user-images.githubusercontent.com/37345589/228598469-35785386-3213-4023-b37c-20af269b8c4d.png)

After applying you should be able to show the image on your Fritzfon under "Menu/Heimnetz/Live-Bild".
Tipp: you can add Live-Bild to favourites  for faster access.

# Donationware:
Feel free to try my Project first and decide how much it is worths to you afterwards.   
www.paypal.me/TimOberle
