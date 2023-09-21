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

# PowerView WIN

Nowe nazwy funkcji

{% embed url="https://harmj4.rssing.com/chan-30881824/article58.html" %}

[https://github.com/PowerShellMafia/PowerSploit/archive/refs/heads/master.zip](https://github.com/PowerShellMafia/PowerSploit/archive/refs/heads/master.zip)

przechodzimy do katalogu gdzie jest skopiowany PowerView

```
cd C:\Users\mike\Desktop\PowerSploit-master\PowerSploit-master\Recon\
```

aby wywołać jakąś fukcje w ramach PowerSploit.ps1 robimy dot sourcing (kropka spacja kropka)

```
. .\PowerView.ps1
```

wylistowanie wszystkich użytkowników

```
Get-DomainUser
```

sprawdzenie nazwy domeny

```
Get-Domain
```

wylistowanie wszystkich użytkowników, których imie zaczyna się na Jess

```
Get-DomainUser -LDAPFilter "(name=Jess*)"
```

wylistowanie użytkownika o danym SID

```
Get-DomainUser -LDAPFilter "(objectsid=S-1-5-21-23434545-435345-345345-115)"
```

pokazanie grupy administratorów domeny

```
Get-DomainObject -Identity "Domain Admins"
```

kto ma prawo co robić na domenie

```
Get-DomainObjectAcl "DC=cyber,DC=local" -ResolveGUIDs
```

co może robić użytkownik o takim lub takim SID

{% code overflow="wrap" %}
```python
Get-DomainObjectAcl "DC=cyber,DC=local"  -ResolveGUIDs | ? { $_.SecurityIdentifier -eq "S-1-5-21-23916123-3291193997-1696429331-1115" -or $_.SecurityIdentifier -eq "S-1-5-21-23916123-3291193997-1696429331-512"}
```
{% endcode %}

wyświetlenie atrybutów użytkownika minniem

```
Get-DomainUser "minniem"
```

sprawdzenie atrybutów Domain Users

```
Get-DomainObject -Identity "Domain Users"
```

jakie atrybuty ma Berlin Office

```
Get-DomainObject "OU=Berlin Office,DC=cyber,DC=local"
```

jakie uprawnienia ma minniem w Berlin Office

{% code overflow="wrap" %}
```python
Get-DomainObjectAcl "OU=Berlin Office,DC=cyber,DC=local" -ResolveGUIDs | ? { $_.SecurityIdentifier -eq "S-1-5-21-23916123-3291193997-1696429331-1115" -or $_.SecurityIdentifier -eq "S-1-5-21-23916123-3291193997-1696429331-512"}
```
{% endcode %}

ciekawe funkcje w PowerView

{% embed url="https://gist.github.com/HarmJ0y/184f9822b195c52dd50c379ed3117993" fullWidth="true" %}
