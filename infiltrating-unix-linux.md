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

# Infiltrating Unix/Linux



```
apt update
apt install metasploit-framework
```

### Spawning a TTY Shell with Python

Interactive Python

```
python -c 'import pty; pty.spawn("/bin/sh")' 
```

### Execution Permissions Considerations

check what `sudo` permissions the account we landed on has:

```
sudo -l
```
