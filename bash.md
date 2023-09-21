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

# bash



```
# Use the latest Ubuntu 22.04 LTS as the base image
FROM ubuntu:22.04

# Update the package repository and install the required packages
RUN apt-get update && \
    apt-get install -y \
        apache2 \
        openssh-server \
        && \
    rm -rf /var/lib/apt/lists/*

# Create a new user called "student"
RUN useradd -m docker-user && \
    echo "docker-user:password" | chpasswd

# Give the htb-student user full access to the Apache and SSH services
RUN chown -R docker-user:docker-user /var/www/html && \
    chown -R docker-user:docker-user /var/run/apache2 && \
    chown -R docker-user:docker-user /var/log/apache2 && \
    chown -R docker-user:docker-user /var/lock/apache2 && \
    usermod -aG sudo docker-user && \
    echo "docker-user ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# Expose the required ports
EXPOSE 22 80

# Start the SSH and Apache services
CMD service ssh start && /usr/sbin/apache2ctl -D FOREGROUND
```

{% code fullWidth="true" %}
```
https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t590-type-20n4-20n5/downloads/driver-list/component?name=BIOS%2FUEFI
==============================================================================
Alpha WiFi

sudo apt install dkms -y
sudo apt-get install realtek-rtl88xxau-dkms
git clone https://github.com/aircrack-ng/rtl8812au.git
sudo make install

==============================================================================
dual boot

sudo os-prober
sudo update-grub
sudo nano /etc/default/grub

dodać na koniec białych linii
GRUB_DISABLE_OS_PROBER=false
sudo update-grub
reboot
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
synology
sudo apt update
sudo apt install nfs-common

sudo nano /etc/fstab

mkdir /mnt/hack

ln -s /mnt/hack /home/hell/Desktop/hack 

192.168.50.115:/volume1/666 /mnt/synology nfs defaults  0  0
============================================================================
SURFSHARK

https://surfshark.com/download/linux

    sudo apt install ./path/to/downloaded/link
    sudo apt update
    sudo apt install surfshark
----------------------------------------------------------------------------
LIBREOFFICE

https://www.libreoffice.org/download/download/

sudo dpkg -i *.deb
----------------------------------------------------------------------------
KEEPASSXC

sudo apt install keepassxc
----------------------------------------------------------------------------
qBitTorrent

sudo apt install qbittorrent
----------------------------------------------------------------------------
VLC

sudo apt install vlc
----------------------------------------------------------------------------
GPARTED

sudo apt install gparted
----------------------------------------------------------------------------
EXODUS

https://www.exodus.com/download/

sudo dpkg -i *.deb
----------------------------------------------------------------------------
GIMP

sudo apt install gimp
----------------------------------------------------------------------------
gThumb

sudo apt install gthumb
----------------------------------------------------------------------------
VIRTUALBOX

sudo apt install virtualbox
sudo apt install -y virtualbox virtualbox-ext-pack
------------------------------------------------------------------------------
TOR

sudo apt install torbrowser-launcher
------------------------------------------------------------------------------
DISKS

sudo apt install -y gnome-disk-utility 
------------------------------------------------------------------------------
GNU Shred

$ sudo shred -vfz /dev/sdX

Shred has many options:

    n - the number of overwrites. The default is three.
    u - overwrite and delete.
    s - the number of bytes to shred.
    v - show extended information.
    f - force the change of permissions to allow writing if necessary.
    z - add a final overwrite with zeros to hide shredding.

Use shred --help for more information
------------------------------------------------------------------------------


```
{% endcode %}
