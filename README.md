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

# FTP

```
sudo apt install vsftpd 
```

{% embed url="http://vsftpd.beasts.org/vsftpd_conf.html" %}

**vsFTPd Config File**

```
cat /etc/vsftpd.conf | grep -v "#"
```

<table><thead><tr><th width="384"></th><th></th></tr></thead><tbody><tr><td><strong>Setting</strong></td><td><strong>Description</strong></td></tr><tr><td><code>listen=NO</code></td><td>Run from inetd or as a standalone daemon?</td></tr><tr><td><code>listen_ipv6=YES</code></td><td>Listen on IPv6 ?</td></tr><tr><td><code>anonymous_enable=NO</code></td><td>Enable Anonymous access?</td></tr><tr><td><code>local_enable=YES</code></td><td>Allow local users to login?</td></tr><tr><td><code>dirmessage_enable=YES</code></td><td>Display active directory messages when users go into certain directories?</td></tr><tr><td><code>use_localtime=YES</code></td><td>Use local time?</td></tr><tr><td><code>xferlog_enable=YES</code></td><td>Activate logging of uploads/downloads?</td></tr><tr><td><code>connect_from_port_20=YES</code></td><td>Connect from port 20?</td></tr><tr><td><code>secure_chroot_dir=/var/run/vsftpd/empty</code></td><td>Name of an empty directory</td></tr><tr><td><code>pam_service_name=vsftpd</code></td><td>This string is the name of the PAM service vsftpd will use.</td></tr><tr><td><code>rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem</code></td><td>The last three options specify the location of the RSA certificate to use for SSL encrypted connections.</td></tr><tr><td><code>rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key</code></td><td></td></tr><tr><td><code>ssl_enable=NO</code></td><td></td></tr></tbody></table>

file is used to deny certain users access to the FTP service

```
cat /etc/ftpusers
----------------------------------
guest
john
kevin
---------------------------------
```

**Anonymous Login**

```
ftp 10.129.14.136
```

<pre><code>#overview of the server's settings
status

#Detailed Output
debug
trace

#Recursive Listing
ls -R

#Download a File
get Important\ Notes.txt

#Download All Available Files
<strong>wget -m --no-passive ftp://anonymous:anonymous@10.129.14.136
</strong>
#Upload a File
put testupload.txt 
</code></pre>

| **Setting**               | **Description**                                                        |
| ------------------------- | ---------------------------------------------------------------------- |
| `dirmessage_enable=YES`   | Show a message when they first enter a new directory?                  |
| `chown_uploads=YES`       | Change ownership of anonymously uploaded files?                        |
| `chown_username=username` | User who is given ownership of anonymously uploaded files.             |
| `local_enable=YES`        | Enable local users to login?                                           |
| `chroot_local_user=YES`   | Place local users into their home directory?                           |
| `chroot_list_enable=YES`  | Use a list of local users that will be placed in their home directory? |

| **Setting**             | **Description**                                                                  |
| ----------------------- | -------------------------------------------------------------------------------- |
| `hide_ids=YES`          | All user and group information in directory listings will be displayed as "ftp". |
| `ls_recurse_enable=YES` | Allows the use of recurse listings.                                              |
