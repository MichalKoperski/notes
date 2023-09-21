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

# dsquery WIN

```
dsquery * DC=cyber,DC=local
```

przeszukanie wszystkich użytkowników w domenie

```
dsquery user DC=cyber,DC=local
```

przeszukanie wszystkich użytkowników w domenie w Organizational Unit New York Office

```
dsquery user "OU=New York Office,DC=cyber,DC=local"
```

przeszukanie wszystkich OU w domenie

```
dsquery OU DC=cyber,DC=local
```

wylistowanie wszystkich atrybutów użytkownika Jessica Rabbit

```
dsquery user "CN=Jessica Rabbit,OU=Berlin Office,DC=cyber,DC=local"
```

**dsquery w wersji graficznej** Windows

```
rundll32.exe dsquery.dll, OpenQueryWindow
```

**Customowy searcher** wklej do Windows PowerShell ISE

{% code overflow="wrap" fullWidth="true" %}
```python
$domainObj = [System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain()

$PDC = ($domainObj.PdcRoleOwner).Name

$SearchString = "LDAP://"

$SearchString += $PDC + "/"

$DistinguishedName = "DC=$($domainObj.Name.Replace('.', ',DC='))"

$SearchString += $DistinguishedName

$Searcher = New-Object System.DirectoryServices.DirectorySearcher([ADSI]$SearchString)

$objDomain = New-Object System.DirectoryServices.DirectoryEntry

$Searcher.SearchRoot = $objDomain

$Searcher.filter="samAccountType=805306368"  #<------------- tutaj możemy wpisać dowolny ldapowy filter. Ten akurat to wyswietlenie wszystkich userow. 

$Searcher.FindAll()
```
{% endcode %}

{% code fullWidth="true" %}
```python
# Uruchamianie skryptu:
$Searcher.FindAll()

# Wyświetlenie pierwszego wyniku
$Searcher.FindAll()[0]

# ZNALEZIENIE KOMPUTERÓW W DOMENIE
$Searcher.Filter="objectclass=computer"
$Searcher.FindAll()

# ZNALEZIENIE ADMINÓW W DOMENIE
$Searcher.Filter="memberOf=CN=Domain Admins, CN=Users, DC=cyber, DC=local"
$Searcher.FindAll()

# ZNALEZIENIE ADMINÓW W DOMENIE których imię zaczyna się na Jess
$Searcher.Filter="(&(memberOf=CN=Domain Admins, CN=Users, DC=cyber, DC=local)(cn=Jess*))"
$Searcher.FindAll()

# ZNALEZIENIE ADMINÓW W DOMENIE których imię nie zaczyna się na Jess
$Searcher.Filter="(&(memberOf=CN=Domain Admins, CN=Users, DC=cyber, DC=local)(!(cn=Jess*)))"
$Searcher.FindAll()
```
{% endcode %}

