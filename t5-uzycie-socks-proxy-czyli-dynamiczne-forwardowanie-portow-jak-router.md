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

# T5 - użycie SOCKS PROXY czyli dynamiczne forwardowanie portów, jak router

<div data-full-width="true">

<figure><img src=".gitbook/assets/1.jpg" alt=""><figcaption></figcaption></figure>

</div>

**Kali** 10.20.10.31

```python
#edytujemy plik proxy chains
vim /etc/proxychains4.conf
socks4 127.0.0.1 9090

ssh -N -D 9090 jessicar@10.20.10.4
```

```python
proxychains rdesktop -d cyber -u jessicar 10.20.10.5
```
