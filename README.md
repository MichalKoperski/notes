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

# progs

tshark - Wireshark w wersji CLI

maltego - zbieranie info, skanuje daną stronę i mówi jaki serwer DNS, jakie odwołania w sieci

[https://book.hacktricks.xyz/welcome/readme](https://book.hacktricks.xyz/welcome/readme)

**contains a list of commands and how they can be exploited through sudo**

[https://gtfobins.github.io/](https://gtfobins.github.io/)

tshark - Wireshark w wersji CLI

tcpdump ograniczamy ilość linijek do 5 i tylko dotyczące kompa 192.168.0.230

```
tcpdump -ni eth0 port 53 -c 5 -r wieshark.pcapng && host 192.168.0.230
```

