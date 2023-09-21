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

# windows

explore the file system

```
dir c:\ /a
```

Displaying Shares using net share

```
net share
```

<table data-full-width="true"><thead><tr><th>Service</th><th>Description</th></tr></thead><tbody><tr><td>smss.exe</td><td>Session Manager SubSystem. Responsible for handling sessions on the system.</td></tr><tr><td>csrss.exe</td><td>Client Server Runtime Process. The user-mode portion of the Windows subsystem.</td></tr><tr><td>wininit.exe</td><td>Starts the Wininit file .ini file that lists all of the changes to be made to Windows when the computer is restarted after installing a program.</td></tr><tr><td>logonui.exe</td><td>Used for facilitating user login into a PC</td></tr><tr><td>lsass.exe</td><td>The Local Security Authentication Server verifies the validity of user logons to a PC or server. It generates the process responsible for authenticating users for the Winlogon service.</td></tr><tr><td>services.exe</td><td>Manages the operation of starting and stopping services.</td></tr><tr><td>winlogon.exe</td><td>Responsible for handling the secure attention sequence, loading a user profile on logon, and locking the computer when a screensaver is running.</td></tr><tr><td>System</td><td>A background system process that runs the Windows kernel.</td></tr><tr><td>svchost.exe with RPCSS</td><td>Manages system services that run from dynamic-link libraries (files with the extension .dll) such as "Automatic Updates," "Windows Firewall," and "Plug and Play." Uses the Remote Procedure Call (RPC) Service (RPCSS).</td></tr><tr><td>svchost.exe with Dcom/PnP</td><td>Manages system services that run from dynamic-link libraries (files with the extension .dll) such as "Automatic Updates," "Windows Firewall," and "Plug and Play." Uses the Distributed Component Object Model (DCOM) and Plug and Play (PnP) services.</td></tr></tbody></table>

Getting SID

```
Get-WmiObject -Class Win32_UserAccount
whoami /user
wmic group get name,sid
```

The SID is broken down into this pattern.

```
(SID)-(revision level)-(identifier-authority)-(subauthority1)-(subauthority2)-(etc)
```

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td><strong>Number</strong></td><td><strong>Meaning</strong></td><td><strong>Description</strong></td></tr><tr><td>S</td><td>SID</td><td>Identifies the string as a SID.</td></tr><tr><td>1</td><td>Revision Level</td><td>To date, this has never changed and has always been <code>1</code>.</td></tr><tr><td>5</td><td>Identifier-authority</td><td>A 48-bit string that identifies the authority (the computer or network) that created the SID.</td></tr><tr><td>21</td><td>Subauthority1</td><td>This is a variable number that identifies the user's relation or group described by the SID to the authority that created it. It tells us in what order this authority created the user's account.</td></tr><tr><td>674899381-4069889467-2080702030</td><td>Subauthority2</td><td>Tells us which computer (or domain) created the number</td></tr><tr><td>1002</td><td>Subauthority3</td><td>The RID that distinguishes one account from another. Tells us whether this user is a normal user, a guest, an administrator, or part of some other group</td></tr></tbody></table>

## Windows Subsystem for Linux (WSL)

```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

### Registry

```
regedit
```

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Value</strong></td><td><strong>Type</strong></td></tr><tr><td>REG_BINARY</td><td>Binary data in any form.</td></tr><tr><td>REG_DWORD</td><td>A 32-bit number.</td></tr><tr><td>REG_DWORD_LITTLE_ENDIAN</td><td>A 32-bit number in little-endian format. Windows is designed to run on little-endian computer architectures. Therefore, this value is defined as REG_DWORD in the Windows header files.</td></tr><tr><td>REG_DWORD_BIG_ENDIAN</td><td>A 32-bit number in big-endian format. Some UNIX systems support big-endian architectures.</td></tr><tr><td>REG_EXPAND_SZ</td><td>A null-terminated string that contains unexpanded references to environment variables (for example, "%PATH%"). It will be a Unicode or ANSI string depending on whether you use the Unicode or ANSI functions. To expand the environment variable references, use the <a href="https://docs.microsoft.com/en-us/windows/win32/api/processenv/nf-processenv-expandenvironmentstringsa"><strong>ExpandEnvironmentStrings</strong></a> function.</td></tr><tr><td>REG_LINK</td><td>A null-terminated Unicode string containing the target path of a symbolic link created by calling the <a href="https://docs.microsoft.com/en-us/windows/desktop/api/Winreg/nf-winreg-regcreatekeyexa"><strong>RegCreateKeyEx</strong></a> function with REG_OPTION_CREATE_LINK.</td></tr><tr><td>REG_MULTI_SZ</td><td>A sequence of null-terminated strings, terminated by an empty string (\0). The following is an example: <em>String1</em>\0<em>String2</em>\0<em>String3</em>\0<em>LastString</em>\0\0 The first \0 terminates the first string, the second to the last \0 terminates the last string, and the final \0 terminates the sequence. Note that the final terminator must be factored into the length of the string.</td></tr><tr><td>REG_NONE</td><td>No defined value type.</td></tr><tr><td>REG_QWORD</td><td>A 64-bit number.</td></tr><tr><td>REG_QWORD_LITTLE_ENDIAN</td><td>A 64-bit number in little-endian format. Windows is designed to run on little-endian computer architectures. Therefore, this value is defined as REG_QWORD in the Windows header files.</td></tr><tr><td>REG_SZ</td><td>A null-terminated string. This will be either a Unicode or an ANSI string, depending on whether you use the Unicode or ANSI functions.</td></tr></tbody></table>

### Local Group Policy

```
gpedit.msc
```
