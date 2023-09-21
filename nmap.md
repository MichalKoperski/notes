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

# nmap

ustali oprogramowanie i jego wersję np ssh ver 2.34

```
nmap -sV
```

uruchamia skrypty, np postara się anonimowo zalogować to jakiejś usługi na badanym ip

```
nmap -sC
```

skanuje wszystkie porty

```
nmap -p-
nmap -p 3333
nmap -p 1-2983
```

skanuje w poszukiwaniu hostów

```
nmap -sn 172.15.0.0/24
```

skryte działanie interwały między wysyłanymi pakietami T0-T5 (najkrótszy interwał)

```
nmap -T4
```
