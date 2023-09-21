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

# Catching Files over HTTP/S

### Nginx - Enabling PUT

Create a Directory to Handle Uploaded Files

```
sudo mkdir -p /var/www/uploads/SecretUploadDirectory
```

Change the Owner to www-data

```
sudo chown -R www-data:www-data /var/www/uploads/SecretUploadDirectory
```

Create the Nginx configuration file by creating the file `/etc/nginx/sites-available/upload.conf` with the contents:

```
server {
    listen 9001;
    
    location /SecretUploadDirectory/ {
        root    /var/www/uploads;
        dav_methods PUT;
    }
}
```

Symlink our Site to the sites-enabled Directory

```
sudo ln -s /etc/nginx/sites-available/upload.conf /etc/nginx/sites-enabled/
```

Start Nginx

```
sudo systemctl restart nginx.service
```

Verifying Errors

```
tail -2 `/var/log/nginx/error.log`
ss -lnpt | grep `80`
ps -ef | grep `2811`
```

Remove NginxDefault Configuration

```
sudo rm /etc/nginx/sites-enabled/default
```

Upload File Using cURL

```
curl -T /etc/passwd http://localhost:9001/SecretUploadDirectory/users.txt
tail -1 /var/www/uploads/SecretUploadDirectory/users.txt 
```
