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

# schtasks - scheduled tasks

{% code overflow="wrap" fullWidth="true" %}
```python
#tworzymy plik .bat w notatniku
schtasks /create /sc minute /mo 1 /tn "PierwszySkrypt" /tr "C:\Users\kali\Desktop\asd.bat" /RU hacker /RP kali /RL HIGHEST

#wylistowanie scheduled tasks
schtasks /query
```
{% endcode %}
