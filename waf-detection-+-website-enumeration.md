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

# WAF detection + Website Enumeration

```python
nmap http-waf-detect

wafw00f http://127.0.0.1/
```

**Dirb**

```python
dirb http://127.0.0.1/

#enumeracja plików php
dirb http://127.0.0.1/ -X php
```

**DirBuster**

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (22).jpg" alt=""><figcaption></figcaption></figure>

</div>

**GoBuster**

{% code fullWidth="true" %}
```python
sudo apt install gobuster

gobuster dir -u "http://127.0.0.1" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php
```
{% endcode %}

**sublist3r**

```python
sublist3r -d http://wp.pl
```
