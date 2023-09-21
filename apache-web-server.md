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

# Apache Web Server



```
sudo apt install apache2 -y
```

For Apache2, to specify which folders can be accessed, we can edit the file

```
/etc/apache2/apache2.conf
```

```
<Directory /var/www/html>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</directory>
```
