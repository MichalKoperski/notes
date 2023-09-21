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

# wfuzz wysyłanie payloadów

{% code overflow="wrap" fullWidth="true" %}
```python
#wfuzz będzie fuzzował na bazie wordlisty XSS.txt tam gdzie jest słowo FUZZ, tylko musimy wpisać swoje "credentiale" tzn przy tej stronie www potrzeba security_level i PHPSESSID
wfuzz -c -z file,/usr/share/wordlists/wfuzz/Iniections/XSS.txt -b "security_level=0; PHPSESSID=h8n53vp2v37" -d "entry=FUZZ&blog=submit&entry_add=" -u http: //127.0.0.1/htmli_stored.php
```
{% endcode %}

zbiór paylodów

[https://github.com/swisskyrepo/PayloadsAl|TheThings](https://github.com/swisskyrepo/PayloadsAl|TheThings)
