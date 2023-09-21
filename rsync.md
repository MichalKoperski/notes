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

# RSYNC

{% embed url="https://book.hacktricks.xyz/network-services-pentesting/873-pentesting-rsync" %}

**Probing for Accessible Shares**

```
nc -nv 127.0.0.1 873
```

**Enumerating an Open Share**

```
rsync -av --list-only rsync://127.0.0.1/dev
```

sync all files

```
rsync -av rsync://127.0.0.1/dev
```

{% embed url="https://phoenixnap.com/kb/how-to-rsync-over-ssh" %}
