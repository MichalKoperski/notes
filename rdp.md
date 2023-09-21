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

# RDP



```
nmap -sV -sC 10.129.201.248 -p3389 --script rdp*

nmap -sV -sC 10.129.201.248 -p3389 --packet-trace --disable-arp-ping -n
```

RDP Security Check

```
sudo cpan

git clone https://github.com/CiscoCXSecurity/rdp-sec-check.git && cd rdp-sec-check
./rdp-sec-check.pl 10.129.201.248
```

**Initiate an RDP Session**

```
xfreerdp /u:cry0l1t3 /p:"P455w0rd!" /v:10.129.201.248
```
