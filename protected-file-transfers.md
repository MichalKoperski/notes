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

# Protected File Transfers

### File Encryption on Windows

Invoke-AESEncryption.ps1

Import Module Invoke-AESEncryption.ps1

```
PS C:\htb> Import-Module .\Invoke-AESEncryption.ps1
```

{% code fullWidth="true" %}
```
.EXAMPLE
Invoke-AESEncryption -Mode Encrypt -Key "p@ssw0rd" -Text "Secret Text" 

Description
-----------
Encrypts the string "Secret Test" and outputs a Base64 encoded ciphertext.
 
.EXAMPLE
Invoke-AESEncryption -Mode Decrypt -Key "p@ssw0rd" -Text "LtxcRelxrDLrDB9rBD6JrfX/czKjZ2CUJkrg++kAMfs="
 
Description
-----------
Decrypts the Base64 encoded string "LtxcRelxrDLrDB9rBD6JrfX/czKjZ2CUJkrg++kAMfs=" and outputs plain text.
 
.EXAMPLE
Invoke-AESEncryption -Mode Encrypt -Key "p@ssw0rd" -Path file.bin
 
Description
-----------
Encrypts the file "file.bin" and outputs an encrypted file "file.bin.aes"
 
.EXAMPLE
Invoke-AESEncryption -Mode Decrypt -Key "p@ssw0rd" -Path file.bin.aes
 
Description
-----------
Decrypts the file "file.bin.aes" and outputs an encrypted file "file.bin"
```
{% endcode %}

### File Encryption on Linux

Encrypting /etc/passwd with openssl

{% code fullWidth="true" %}
```
michal86@htb[/htb]$ openssl enc -aes256 -iter 100000 -pbkdf2 -in /etc/passwd -out passwd.enc
```
{% endcode %}

Decrypt passwd.enc with openssl

{% code fullWidth="true" %}
```
michal86@htb[/htb]$ openssl enc -d -aes256 -iter 100000 -pbkdf2 -in passwd.enc -out passwd    
```
{% endcode %}
