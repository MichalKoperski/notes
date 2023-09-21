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

# john

{% code fullWidth="true" %}
```python
john --wordlist=list -format=RAW-MD5 password.txt

#wyciągnięcie hasha z rar
rar2john a.rar > rar.hash

#wyciągnięcie z pdf
pdf2john a.pdf > pdf.hash

#wyciągnięcie z ssh
ssh2john
```
{% endcode %}
