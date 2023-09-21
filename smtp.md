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

# SMTP

**Default Configuration**\


```
cat /etc/postfix/main.cf | grep -v "#" | sed -r "/^\s*$/d"
```

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Command</strong></td><td><strong>Description</strong></td></tr><tr><td><code>AUTH PLAIN</code></td><td>AUTH is a service extension used to authenticate the client.</td></tr><tr><td><code>HELO</code></td><td>The client logs in with its computer name and thus starts the session.</td></tr><tr><td><code>MAIL FROM</code></td><td>The client names the email sender.</td></tr><tr><td><code>RCPT TO</code></td><td>The client names the email recipient.</td></tr><tr><td><code>DATA</code></td><td>The client initiates the transmission of the email.</td></tr><tr><td><code>RSET</code></td><td>The client aborts the initiated transmission but keeps the connection between client and server.</td></tr><tr><td><code>VRFY</code></td><td>The client checks if a mailbox is available for message transfer.</td></tr><tr><td><code>EXPN</code></td><td>The client also checks if a mailbox is available for messaging with this command.</td></tr><tr><td><code>NOOP</code></td><td>The client requests a response from the server to prevent disconnection due to time-out.</td></tr><tr><td><code>QUIT</code></td><td>The client terminates the session.</td></tr></tbody></table>

To interact with the SMTP server, we can use the `telnet` tool to initialize a TCP connection with the SMTP server.

**Telnet - HELO/EHLO**

```
telnet 10.129.14.128 25

#EHLO
EHLO mail1

#command VRFY can be used to enumerate existing users on the system
VRFY root
```

command `VRFY` can be used to enumerate existing users on the system

```
VRFY root
```

nmap

```
sudo nmap 10.129.14.128 -p25 --script smtp-open-relay -v
```

Use the VRFY method (`-M VRFY`) to search for the specified user (`-u root`) on the target server (`-t 192.168.1.25`):

```
smtp-user-enum -M VRFY -u root -t 192.168.1.25
smtp-user-enum -M VRFY -U users.txt -t 10.0.0.1
```
