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

# NFS

```
sudo apt install nfs-kernel-server -y
```

```
systemctl status nfs-kernel-server
```

contains a table of physical filesystems on an NFS server accessible by the clients

```
cat /etc/exports 
```

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Option</strong></td><td><strong>Description</strong></td></tr><tr><td><code>rw</code></td><td>Read and write permissions.</td></tr><tr><td><code>ro</code></td><td>Read only permissions.</td></tr><tr><td><code>sync</code></td><td>Synchronous data transfer. (A bit slower)</td></tr><tr><td><code>async</code></td><td>Asynchronous data transfer. (A bit faster)</td></tr><tr><td><code>secure</code></td><td>Ports above 1024 will not be used.</td></tr><tr><td><code>insecure</code></td><td>Ports above 1024 will be used.</td></tr><tr><td><code>no_subtree_check</code></td><td>This option disables the checking of subdirectory trees.</td></tr><tr><td><code>root_squash</code></td><td>Assigns all permissions to files of root UID/GID 0 to the UID/GID of anonymous, which prevents <code>root</code> from accessing files on an NFS mount.</td></tr></tbody></table>

We have shared the folder `/mnt/nfs` to the subnet `10.129.14.0/24` with the setting shown above

```
echo '/mnt/nfs  10.129.14.0/24(sync,no_subtree_check)' >> /etc/exports
systemctl restart nfs-kernel-server 
exportfs
-----------------------------------------
/mnt/nfs      	10.129.14.0/24
-----------------------------------------
```

### Dangerous Settings

| **Option**       | **Description**                                                                                                      |
| ---------------- | -------------------------------------------------------------------------------------------------------------------- |
| `rw`             | Read and write permissions.                                                                                          |
| `insecure`       | Ports above 1024 will be used.                                                                                       |
| `nohide`         | If another file system was mounted below an exported directory, this directory is exported by its own exports entry. |
| `no_root_squash` | All files created by root are kept with the UID/GID 0.                                                               |

nmap

```
nmap --script nfs* 10.129.14.128 -sV -p111,2049
```

**Show Available NFS Shares**

```
showmount -e 10.129.14.128
```

**Mounting NFS Share**

```
mkdir target-NFS
sudo mount -t nfs 10.129.14.128:/ ./target-NFS/ -o nolock
cd target-NFS
tree .
```

**List Contents with Usernames & Group Names**

```
ls -l mnt/nfs/

#List Contents with UIDs & GUIDs
ls -n mnt/nfs/
```

**Unmounting**

```
cd ..
sudo umount ./target-NFS
```
