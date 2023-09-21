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

# Infiltrating Windows

{% embed url="https://subinsb.com/default-device-ttl-values/" %}

OS Detection Scan

```
sudo nmap -v -O 192.168.86.39
```

Banner Grab to Enumerate Ports

```
sudo nmap -v 192.168.86.39 --script banner.nse
```

Use `CMD` when:

* You are on an older host that may not include PowerShell.
* When you only require simple interactions/access to the host.
* When you plan to use simple batch files, net commands, or MS-DOS native tools.
* When you believe that execution policies may affect your ability to run scripts or other actions on the host.

Use `PowerShell` when:

* You are planning to utilize cmdlets or other custom-built scripts.
* When you wish to interact with .NET objects instead of text output.
* When being stealthy is of lesser concern.
* If you are planning to interact with cloud-based services and hosts.
* If your scripts set and use Aliases.
