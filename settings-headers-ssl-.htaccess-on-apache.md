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

# settings/headers/ssl .htaccess on Apache

{% code overflow="wrap" fullWidth="true" %}
```python
127.0.0.1/server-status

#wyłączenie pokazywania wersji servera
sudo nano /etc/apache2/apache2.conf
ServerSignature Off
ServerTokens Prod

#włączanie nagłówków
a2enmod headers
  #Clickiacking
  X-FRAME-OPTIONS
  #XSS
  Header set X-XSS-PROTECTION: "1; mode=block"
  #HSTS
  STRICT-TRANSPORT-SECURITY
  #Content
  X-CONTENT-TYPE-OPTIONS
  #same origin policy
  Header append X-Frame-Options: "SAMEORIGIN"
  
#żeby właczyć używanie .htaccess
touch /var/www/html/.htaccess

sudo nano /etc/apache2/apache2.conf
<Directory /var /www/>
AllowOverride All

#wyłączanie 1. indexowania 2. co jak wejdziemy w stronę której nie ma 3.zakaz dostępu z ip 10.0.20.10
sudo nano .htaccess
Options -Indexes
ErrorDocument 404 /notfound.html
Deny From 10.0.20.10

#wyłaczanie server-status
sudo a2dismod status
```
{% endcode %}

{% code fullWidth="true" %}
```python
#generowanie certyfikatu SSL
openssl req -x509 -nodes -days 365 -newkey rsa: 2048 -keyout /etc/ss1/private/apache-
selfsigned.key -out /etc/ssl/certs/apache-selfsigned.crt

#dodajemy linijki w default-ssl.conf
sudo nano /etc/apache2/sites-available/default-ssl.conf
ServerName 127.6.6.1

SSLCertificateFile /etc/ssl/certs/apache-selfsigned.crt
SSLCertificateKeyFile/etc/ssl/private/apache-selfsigned.key

#komenda
a2enmod ssl
```
{% endcode %}

{% code fullWidth="true" %}
```python
#edycja ustawień php
sudo nano /etc/php/8.1/apache2/php.ini

#Vulnerable Functions
eval() 
include()
include_once()
require()
require_once() 
exec()
system()

#Information Disclosure
display_errors = 0
display_startup_errors = 0

#Unrestricted File Upload
file_uploads = 1
upload_max_filesize = 1M

#Remote Code Execution
disable_functions = [functions]

#Remote File Inclusion
allow_url_fopen = Off
allow_url_include = Off

#Distributed Denial of Service
max_execution_time = 30
memory_limit = 8M
```
{% endcode %}

| Web Server | Default Webroot        |
| ---------- | ---------------------- |
| `Apache`   | /var/www/html/         |
| `Nginx`    | /usr/local/nginx/html/ |
| `IIS`      | c:\inetpub\wwwroot\\   |
| `XAMPP`    | C:\xampp\htdocs\\      |
