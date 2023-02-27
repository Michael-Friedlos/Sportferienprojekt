# Sportferienprojekt Raspberry PI als Access Point



## Raspbian/PiOS auf den neusten Stand bringen

```
sudo apt-get update
sudo apt-get upgrade
```



## Raspi neu starten

```
reboot

```



## Hostapd installieren

```
sudo apt install hostapd

```



## Dnsmasq installieren

```
sudo apt install dnsmasq

```



## Beides stoppen

```
sudo systemctl stop hostapd
sudo systemctl stop dnsmasq
```



## Hostapd mit Nano bearbeiten

```
sudo nano /etc/hostapd/hostapd.conf
```



## Hostapd configurieren

```
interface=wlan0
driver=nl80211
ssid=RPiHotSpot
hw_mode=g
channel=6
wmm_enabled=0
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=1234567890
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP
```




## Hostapd Service Unmask'en

```
sudo systemctl unmask hostapd
sudo systemctl enable hostapd
```



## Dnsmasq mit Nano öffnen

```
sudo nano /etc/dnsmasq.conf
```



## Dnsmasq Configurieren

```
#RPiHotspot config - Internet
interface=wlan0
bind-dynamic 
domain-needed
bogus-priv
dhcp-range=192.168.50.150,192.168.50.200,255.255.255.0,12h
```



## Interfaces öffnen

```
sudo nano /etc/network/interfaces
```



## Alles in der Interfaces Datei kopieren

```
# interfaces(5) file used by ifup(8) and ifdown(8)
# Please note that this file is written to be used with dhcpcd
# For static IP, consult /etc/dhcpcd.conf and 'man dhcpcd.conf'
# Include files from /etc/network/interfaces.d:
source-directory /etc/network/interfaces.d

```



## Rüberkopieren in die Datei "interfaces-backup"

```
sudo cp /etc/network/interfaces /etc/network/interfaces-backup

```



## Dhcpcd mit Nano öffnen

```
sudo nano /etc/dhcpcd.conf


```



## Folgendes zuunterst eifügen

```
interface wlan0
nohook wpa_supplicant
static ip_address=192.168.50.10/24
static routers=192.168.50.1
static domain_name_servers=8.8.8.8

```



## Sysctl configurieren mit Nano

```
sudo nano /etc/sysctl.conf

```



## Das # entfernen bei "#net.ipv4.ip_forward=1"

```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```



## File erstellen für die IP Table Reglen

```
sudo nano /etc/iptables-hs

```



## Folgendes in die Datei einfügen

```
#!/bin/bash
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth0 -o wlan0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i wlan0 -o eth0 -j ACCEPT

```



## Erlaubniss ändern

```
sudo chmod +x /etc/iptables-hs

```



## Folgendes File erstellen

```
sudo nano /etc/systemd/system/hs-iptables.service


```



## Folgendes dort einfügen

```
[Unit]
Description=Activate IPtables for Hotspot
After=network-pre.target
Before=network-online.target

[Service]
Type=simple
ExecStart=/etc/iptables-hs

[Install]
WantedBy=multi-user.target

```



## Service aktivieren das er bei jedem Starten automatisch beginnt

```
sudo systemctl enable hs-iptables

```



## Reboot'en un schauen obs funktioniert

```
reboot

```



### Anleitung von https://www.raspberryconnect.com/projects/65-raspberrypi-hotspot-accesspoints/168-raspberry-pi-hotspot-access-point-dhcpcd-method