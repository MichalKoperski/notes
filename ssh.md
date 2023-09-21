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

# SSH

{% embed url="https://www.golinuxcloud.com/openssh-authentication-methods-sshd-config/" %}

```
sudo apt install openssh-server -y
```

```
systemctl status ssh
```

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

**Default Configuration**

```
cat /etc/ssh/sshd_config  | grep -v "#" | sed -r '/^\s*$/d'
```

### Dangerous Settings

| **Setting**                  | **Description**                             |
| ---------------------------- | ------------------------------------------- |
| `PasswordAuthentication yes` | Allows password-based authentication.       |
| `PermitEmptyPasswords yes`   | Allows the use of empty passwords.          |
| `PermitRootLogin yes`        | Allows to log in as the root user.          |
| `Protocol 1`                 | Uses an outdated version of encryption.     |
| `X11Forwarding yes`          | Allows X11 forwarding for GUI applications. |
| `AllowTcpForwarding yes`     | Allows forwarding of TCP ports.             |
| `PermitTunnel`               | Allows tunneling.                           |
| `DebianBanner yes`           | Displays a specific banner when logging in. |

**SSH-Audit**

```
git clone https://github.com/jtesta/ssh-audit.git && cd ssh-audit
./ssh-audit.py 10.129.14.132
```

Change Authentication Method

```
ssh -v cry0l1t3@10.129.14.132

ssh -v cry0l1t3@10.129.14.132 -o PreferredAuthentications=password
```

