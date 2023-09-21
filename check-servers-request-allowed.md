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

# check server’s request allowed

```python
nmap -p80 --script http-methods 127.0.0.1
nmap -p80 --script http-enum 127.0.0.1

curl -i -X OPTIONS -L http://10.1.20.13
```
