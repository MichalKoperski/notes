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

# nmap

```python
#normal output
-oN wynik.txt

#XML output
-oX

#script kiddie output
-oS

#grepable output
-oG

#output to all formats
-oA

#xmas scan, nie wykrywalny przez IDS/IPS, wysyła pakiety FIN, PSH, URG
-sX

#stealth scan pakiety SYN
-sS

#zapytania FIN
-sF

#wykorzystuje komputer zombie żeby zamaskować swoje działanie
nmap -sI IP_ZOMBIE 10.20.10.12

#wykorzystanie skryptów np szukanie vulnerabilities
nmap --script vuln 10.10.20.10

#szuaknie na niektórych ip
nmap 10.20.10-30,45.5/16

#omijanie niektórych ip zapisanych w pliku list
--excludefile list

#scan po protokole TCP SYN
-PS

#scan po protokole TCP ACK
-PA

#scan po protokole UDP
-PU

#wykrywanie aktywnych hostów
nmap -sn 192.168.0.0/24

#wersja danego serwisu
--version-all -sV

#jaki system operacyjny na hoscie
-O

#agresywny skan
-A

#banner grabbing
--script banner
#lub
nc -nv 10.0.4.7 80

#enumerate common web application directories
--script=http-enum
```
