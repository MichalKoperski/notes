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

# linux

## Getting Help

```
man <tool>
man curl

<tool> --help
curl --help

<tool> -h
curl -h

apropos <keyword>
apropos sudo
```

{% embed url="https://explainshell.com/" %}

<table data-full-width="true"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Command</strong></td><td><strong>Description</strong></td></tr><tr><td><code>whoami</code></td><td>Displays current username.</td></tr><tr><td><code>id</code></td><td>Returns users identity</td></tr><tr><td><code>hostname</code></td><td>Sets or prints the name of current host system.</td></tr><tr><td><code>uname</code></td><td>Prints basic information about the operating system name and system hardware.</td></tr><tr><td><code>pwd</code></td><td>Returns working directory name.</td></tr><tr><td><code>ifconfig</code></td><td>The ifconfig utility is used to assign or to view an address to a network interface and/or configure network interface parameters.</td></tr><tr><td><code>ip</code></td><td>Ip is a utility to show or manipulate routing, network devices, interfaces and tunnels.</td></tr><tr><td><code>netstat</code></td><td>Shows network status.</td></tr><tr><td><code>ss</code></td><td>Another utility to investigate sockets.</td></tr><tr><td><code>ps</code></td><td>Shows process status.</td></tr><tr><td><code>who</code></td><td>Displays who is logged in.</td></tr><tr><td><code>env</code></td><td>Prints environment or sets and executes command.</td></tr><tr><td><code>lsblk</code></td><td>Lists block devices.</td></tr><tr><td><code>lsusb</code></td><td>Lists USB devices</td></tr><tr><td><code>lsof</code></td><td>Lists opened files.</td></tr><tr><td><code>lspci</code></td><td>Lists PCI devices.</td></tr></tbody></table>

What is the path to the htb-student's mail

{% code overflow="wrap" fullWidth="true" %}
```
#What is the path to the htb-student's mail
env | grep MAIL

#Which shell is specified for the htb-student user?
env | grep SHELL

#What is the index number of the "sudoers" file in the "/etc" director
ls -i sudoers

#The command mkdir has an option marked -p to add parent directories.
mkdir -p Storage/local/user/documents

#We can also create files directly in the directories by specifying the path where the file should be stored. The trick is to use the single dot (.) to tell the system that we want to start from the current directory
touch ./Storage/local/user/userinfo.txt

#Move Files to Specific Directory
mv information.txt readme.txt Storage/

#How many total packages are installed on the target system?
dpkg -l | grep -c '^ii'

#to exclude specific results
cat /etc/passwd | grep -v "false\|nologin"

#awk programming is beneficial, which allows us to display the first ($1) and last ($NF) result of the line.
cat /etc/passwd | grep -v "false\|nologin" | tr ":" " " | awk '{print $1, $NF}'

#How many services are listening on the target system on all interfaces? (Not on localhost and IPv4 only)
netstat -tunleep4 | grep -v "127\.0\.0"

#Use cURL from your Pwnbox (not the target machine) to obtain the source code of the "https://www.inlanefreight.com" website and filter all unique paths of that domain. Submit the number of these paths as the answer.
curl https://www.inlanefreight.com/ | grep -Po "https://www.inlanefreight.com/[^'\"]*" | sort -u | wc -l

#Which option needs to be set to execute a command as a different user using the "su" command
su --command
```
{% endcode %}

### Which

```
which python
```

### Find

{% code fullWidth="true" %}
```
find <location> <options>
find / -type f -name *.conf -user root -size +20k -newermt 2020-03-03 -exec ls -al {} \; 2>/dev/null
```
{% endcode %}

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Option</strong></td><td><strong>Description</strong></td></tr><tr><td><code>-type f</code></td><td>Hereby, we define the type of the searched object. In this case, '<code>f</code>' stands for '<code>file</code>'.</td></tr><tr><td><code>-name *.conf</code></td><td>With '<code>-name</code>', we indicate the name of the file we are looking for. The asterisk (<code>*</code>) stands for 'all' files with the '<code>.conf</code>' extension.</td></tr><tr><td><code>-user root</code></td><td>This option filters all files whose owner is the root user.</td></tr><tr><td><code>-size +20k</code></td><td>We can then filter all the located files and specify that we only want to see the files that are larger than 20 KiB.</td></tr><tr><td><code>-newermt 2020-03-03</code></td><td>With this option, we set the date. Only files newer than the specified date will be presented.</td></tr><tr><td><code>-exec ls -al {} \;</code></td><td>This option executes the specified command, using the curly brackets as placeholders for each result. The backslash escapes the next character from being interpreted by the shell because otherwise, the semicolon would terminate the command and not reach the redirection.</td></tr><tr><td><code>2>/dev/null</code></td><td>This is a <code>STDERR</code> redirection to the '<code>null device</code>', which we will come back to in the next section. This redirection ensures that no errors are displayed in the terminal. This redirection must <code>not</code> be an option of the 'find' command.</td></tr></tbody></table>

### Locate

```
sudo updatedb
locate *.conf
```

### File Descriptors

1. Data Stream for Input
   * `STDIN – 0`
2. Data Stream for Output
   * `STDOUT – 1`
3. Data Stream for Output that relates to an error occurring.
   * `STDERR – 2`

we use the `find` command to search for all files in the "`/etc/`" directory with a "`.conf`" extension. Any errors are redirected to the "`null device`" (`/dev/null`). Using `grep`, we filter out the results and specify that only the lines containing the pattern "`systemd`" should be displayed.\


```
find /etc/ -name *.conf 2>/dev/null | grep systemd
```

we will use the tool called `wc`, which should count the total number of obtained results.

```
find /etc/ -name *.conf 2>/dev/null | grep systemd | wc -l
```

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Command</strong></td><td><strong>Description</strong></td></tr><tr><td><code>sudo</code></td><td>Execute command as a different user.</td></tr><tr><td><code>su</code></td><td>The <code>su</code> utility requests appropriate user credentials via PAM and switches to that user ID (the default user is the superuser). A shell is then executed.</td></tr><tr><td><code>useradd</code></td><td>Creates a new user or update default new user information.</td></tr><tr><td><code>userdel</code></td><td>Deletes a user account and related files.</td></tr><tr><td><code>usermod</code></td><td>Modifies a user account.</td></tr><tr><td><code>addgroup</code></td><td>Adds a group to the system.</td></tr><tr><td><code>delgroup</code></td><td>Removes a group from the system.</td></tr><tr><td><code>passwd</code></td><td>Changes user password.</td></tr></tbody></table>

### Git

```
mkdir ~/nishang/ && git clone https://github.com/samratashok/nishang.git ~/nishang
```

### DPKG

{% code fullWidth="true" %}
```
wget http://archive.ubuntu.com/ubuntu/pool/main/s/strace/strace_4.21-1ubuntu1_amd64.deb
sudo dpkg -i strace_4.21-1ubuntu1_amd64.deb 
```
{% endcode %}

### Kill a Process

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Signal</strong></td><td><strong>Description</strong></td></tr><tr><td><code>1</code></td><td><code>SIGHUP</code> - This is sent to a process when the terminal that controls it is closed.</td></tr><tr><td><code>2</code></td><td><code>SIGINT</code> - Sent when a user presses <code>[Ctrl] + C</code> in the controlling terminal to interrupt a process.</td></tr><tr><td><code>3</code></td><td><code>SIGQUIT</code> - Sent when a user presses <code>[Ctrl] + D</code> to quit.</td></tr><tr><td><code>9</code></td><td><code>SIGKILL</code> - Immediately kill a process with no clean-up operations.</td></tr><tr><td><code>15</code></td><td><code>SIGTERM</code> - Program termination.</td></tr><tr><td><code>19</code></td><td><code>SIGSTOP</code> - Stop the program. It cannot be handled anymore.</td></tr><tr><td><code>20</code></td><td><code>SIGTSTP</code> - Sent when a user presses <code>[Ctrl] + Z</code> to request for a service to suspend. The user can handle it afterward.</td></tr></tbody></table>

```
kill 9 <PID> 
```

## Task Scheduling

Create a Timer

```
sudo mkdir /etc/systemd/system/mytimer.timer.d
sudo nano /etc/systemd/system/mytimer.timer
```

mytimer.timer

```
[Unit]
Description=My Timer

[Timer]
OnBootSec=3min
OnUnitActiveSec=1hour

[Install]
WantedBy=timers.target
```

{% hint style="info" %}
&#x20;if we want to run our script only once after the system boot, we should use `OnBootSec` setting in `Timer`. However, if we want our script to run regularly, then we should use the `OnUnitActiveSec` to have the system run the script at regular intervals. Next, we need to create our `service`
{% endhint %}

Create a Service

```
sudo nano /etc/systemd/system/mytimer.service
```

mytimer.service

```
[Unit]
Description=My Service

[Service]
ExecStart=/full/path/to/my/script.sh

[Install]
WantedBy=multi-user.target
```

{% hint style="info" %}
The "multi-user.target" is the unit system that is activated when starting a normal multi-user mode. It defines the services that should be started on a normal system startup.
{% endhint %}

Reload Systemd

```
sudo systemctl daemon-reload
```

Start the Timer & Service

```
sudo systemctl start mytimer.service
sudo systemctl enable mytimer.service
```

**Fdisk**

```
sudo fdisk -l
```

**Mounted File systems at Boot**

```
cat /etc/fstab

mount
```

Mount a USB drive

```
sudo mount /dev/sdb1 /mnt/usb
```

Unmount

```
sudo umount /mnt/usb
```

## Network Configuration

Activate Network Interface

```
sudo ifconfig eth0 up
sudo ip link set eth0 up
```

Assign IP Address to an Interface

```
sudo ifconfig eth0 192.168.1.2
```

Assign a Netmask to an Interface

```
sudo ifconfig eth0 netmask 255.255.255.0
```

Assign the Route to an Interface

```
sudo route add default gw 192.168.1.1 eth0
```

Editing Interfaces

```
sudo nano /etc/network/interfaces
```

```
auto eth0
iface eth0 inet static
  address 192.168.1.2
  netmask 255.255.255.0
  gateway 192.168.1.1
  dns-nameservers 8.8.8.8 8.8.4.4
```

Restart Networking Service

```
sudo systemctl restart networking
```
