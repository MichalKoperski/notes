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

# wordpress

{% code fullWidth="true" %}
```python
127.0.0.1/wp-config.php
127.0.0.1/wp-admin/profile.php
127.0.0.1/?author=0
```
{% endcode %}

**wpscan**

{% code fullWidth="true" %}
```python
#skanuje na podatne themes i plugins
wpscan --url http://10.1.20.27:9999/wordpress -e vp vt

#brute-force haseł
wpscan --url http://127.0.0.1 -U 'michal' -p /usr/share/wordlists/metasploit/burnett_top_1024.txt

#perform enumeration for themes and plugins AGGRESIVE version
wpscan --url http://127.0.0.1 -e ap --plugins-detection aggressive

#enumerate only users with an "ID" in the range of 1 to 5 flags
wpscan --url http://127.0.0.1 -e u1-5
#albo poprzez proxy żeby przechwycić przez burp suit
wpscan --url http://127.0.0.1 -e u1-5 --proxy http://127.0.0.1:8080
```
{% endcode %}
