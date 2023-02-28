# Sportferienprojekt Raspberry PI als Access Point



## Raspbian/PiOS auf den neusten Stand bringen

```
sudo apt update
sudo apt upgrade -y
```


## raspi-config verwenden um den Raspberry PI zu bearbeiten

```
sudo raspi-config

```



## Gehe nun mit den Pfeiltasten zu Advanced Options und klicke dann enter

![Problem with loading the image](/images/Bild_1.webp "Gehe nun mit den Pfeiltasten zu Advanced Options und klicke dann enter")



## Gehe dann zu Network Config und klicke abermals Enter

![Problem with loading the image](/images/Bild_2.webp "Gehe dann zu Network Config und klicke abermals Enter")



## Wähle Network Manager und klicke dann Ok

![Problem with loading the image](/images/Bild_3.webp "Wähle Network Manager und klicke dann Ok")



## Klicke wieder Ok

![Problem with loading the image](/images/Bild_4.webp "Klicke wieder Ok")



## Klicke Finish

![Problem with loading the image](/images/Bild_5.webp "Klicke Finish")



## Wähle yes und Starte so das System neu

![Problem with loading the image](/images/Bild_6.webp "Wähle yes und Starte so das System neu")



## Klicke mit der linken Maustaste auf das Netzwerk-Icon, wähle Advanced Options und erstelle dann einen Wireless Hotspot

![Problem with loading the image](/images/Bild_7.webp "Klicke mit der linken Maustaste auf das Netzwerk-Icon, wähle Advanced Options und erstelle dann einen Wireless Hotspot")



## Setze den Namen des Access Points, Wi-Fi Sicherheit auf WPA2 und setze dann das Passwort für den AP. Klicke Create um dies zu speichern

![Problem with loading the image](/images/Bild_8.webp "Setze den Namen des Access Points, Wi-Fi Sicherheit auf WPA2 und setze dann das Passwort für den AP. Klicke Create um dies zu speichern")



## Starte den Raspberry PI neu



## Klicke auf das Netzwerk-Icon um zu sehen ob der Access Point activ ist

![Problem with loading the image](/images/Bild_9.webp "Klicke auf das Netzwerk-Icon um zu sehen ob der Access Point activ ist")



## Klicke wieder auf das Netzwerk-Icon und dann auf Advanced Options -> Edit Connections.

![Problem with loading the image](/images/Bild_10.webp "Klicke wieder auf das Netzwerk-Icon und dann auf Advanced Options -> Edit Connections.")



## Wähle den Namen des Access Points und klicke auf den Einstellungen Button um einstellungen vorzunehmen.

![Problem with loading the image](/images/Bild_11.webp "Wähle den Namen des Access Points und klicke auf den Einstellungen Button um einstellungen vorzunehmen.")



## Gehe nun zum Abteil General, activiere "Connect automatically with priority" und setze die Priorität auf 0. Sichere am Schluss die vorgenommenen Änderungen

![Problem with loading the image](/images/Bild_12.webp "Gehe nun zum Abteil General, activiere Connect automatically with priority und setze die Priorität auf 0. Sichere am Schluss die vorgenommenen Änderungen")



## Nun kannst du dich mit deinem beliebigen Gerät unter Wlan mit dem Wi-Fi des Raspberry PI's verbinden, sofern er eingeschaltet ist.



## Um die Infos über das Wi-Fi ersichtlich zu machen, klicke abermals auf das Netzwerk-Icon und dann auf Advanced Options -> Connection Information. 

![Problem with loading the image](/images/Bild_13.webp "Um die Infos über das Wi-Fi ersichtlich zu machen, klicke abermals auf das Netzwerk-Icon und dann auf Advanced Options -> Connection Information")



## Nun siehst du die Infos zu dem Wi-Fi deines Raspberry PI's. Scanne mit einem beliebigen Gerät den vorhandenen QR Code und verbinde dich so automatisch mit dem Wi-Fi des Raspberry PI's

![Problem with loading the image](/images/Bild_14.webp "Nun siehst du die Infos zu dem Wi-Fi deines Raspberry PI's. Scanne mit einem beliebigen Gerät den vorhandenen QR Code und verbinde dich so automatisch mit dem Wi-Fi des Raspberry PI's")



### Anleitung von https://www.tomshardware.com/how-to/raspberry-pi-access-point