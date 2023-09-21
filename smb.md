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

# smb

{% code overflow="wrap" fullWidth="true" %}
```python
#The -L flag specifies that we want to retrieve a list of available shares on the remote host, while -N suppresses the password prompt.
smbclient -N -L \\\\10.129.42.253

#łączenie z danym zasobem użytkownikiem bob
smbclient -U bob \\\\10.129.42.253\\users
```
{% endcode %}
