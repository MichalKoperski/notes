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

# hydra - crackowanie loginów stron

{% code fullWidth="true" %}
```
#crackowanie hasła antyjanusza na stronie 127.0.0.1 przy użyciu 4 wątków jednocześnie
-l - pojedynczy użytkownik
-L - lista użytkowników czyli musimy się odwołać do pliku tekstowego
-p - pojedyncze hasło
-P - lista haseł czyli musimy się odwołać do pliku tekstowego

sudo hydra -l antyjanusz -P /usr/share/wordlists/rockyou.txt 127.0.0.1 -t 4 ssh -v
```
{% endcode %}
