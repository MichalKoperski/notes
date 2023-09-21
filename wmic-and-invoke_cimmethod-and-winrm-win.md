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

# wmic & Invoke\_CimMethod & WinRM WIN

**wmic**

{% code overflow="wrap" fullWidth="true" %}
```
#help
wmic /?

#wylistowanie wszystkich procesów
wmic process list brief

#tworzenie procesu kalkulator
wmic process call create "calc.exe"

#zamykanie procesu kalkulatora
wmic process where name="calc.exe" call terminate

#wylistowanie procesów na zdalnym komputerze
wmic /node:10.20.10.5 /user:jessicar /password:Aa123456! process list brief

#wylistowanie userów
wmic /node:10.20.10.5 /user:jessicar /password:Aa123456! useraccount list

#provide network information
wmic nicconfig get ipaddress, macaddress

#retrieve a full startup list
wmic startup list full

#lists users and groups
wmic useraccount/group/sysaccount list

#gets a Shared Folder list
wmic share list

#lists services
wmic service list brief

#lists local accounts
wmic /record:users_lisr.xml useraccount list

#uruchomienie kalkulatora na zdalnym komputerze
wmic /node:10.20.10.5 /user:jessicar /password:Aa123456! process call create "calc.exe"

#zamykanie procesu na zdalnym komputerze
wmic /node:10.20.10.5 /user:jessicar /password:Aa123456! process where processId=1311 call terminate
```
{% endcode %}

**cim** PowerShell

{% code overflow="wrap" fullWidth="true" %}
```
#wylistowanie klas cim
Get-CimClass

#wylistowanie procesów
Get-CimClass |select-string "Process"

#wylistowanie atrybutów Win32_Process
Get-CimClass -ClassName "Win32_Process"
Get-CimClass -ClassName "Win32_Process" |select -ExpandProperty CimClassMethods

#uruchomienie Powershell
Invoke-CimMethod -ClassName "Win32_Process" -MethodName "Create" -Arguments @{CommandLine = "Powershell.exe"}

#uruchomienie cmd i zapytanie whoami
Invoke-CimMethod -ClassName "Win32_Process" -MethodName "Create" -Arguments @{CommandLine = "cmd.exe /k whoami"}

#uruchomienie cmd na zdalnym komputerze
Invoke-CimMethod -ClassName "Win32_Process" -MethodName "Create" -Arguments @{CommandLine = "cmd.exe /k whoami"} -ComputerName WIN-213
```
{% endcode %}

**WinRM**

{% code overflow="wrap" fullWidth="true" %}
```
winrm quickconfig
Enable-PSRemoting -Force
Set-Item WSMan:\localhost\Client\TrustedHosts
Enter-PSSession -ComputerName "PC1" -Credential "Lisa"

#tworzenie katalogu na komputerze zdalnym
Invoke-Command -ComputerName PC1 -ScriptBlock {mkdir C:\Users\mike\Desktop\test}

#wylistowanie procesów na zdalnym komputerze
Invoke-Command -ComputerName PC1 -ScriptBlock {GetProcess}

#wejście na zdalny komputer
Enter-PSSession -ComputerName PC1

#tworzenie kilka sesji
New-PSSession -ComputerName PC1
New-PSSession -ComputerName PC2

#wylistowanie wszystkich aktywnych sesji
Get-PSSession

#wejście do sesji 10
Enter-PSSession -Id 10

#kończenie sesji nr 10
exit
Remove-PSSesion -Id 10

#tworzenie nowego usera na Desktop-1
Invoke-Command -ComputerName "Desktop-1" -ScriptBlock {net user hacker Aa12345 /add}

#wejście na komputer zdalny za pomocą hasła innego użytkownika
$password = ConvertTo-SecureString "Aa123456!" -AsPlainText -Force
$creds = New-Object System.Management.Automation.PSCredential("jessicar", $password)
Enter-PSSession -ComputerName WIN-172198 -Credential $creds
```
{% endcode %}
