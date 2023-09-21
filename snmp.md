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

# SNMP

### Default Configuration

```
cat /etc/snmp/snmpd.conf | grep -v "#" | sed -r '/^\s*$/d'
```

### Dangerous Settings

| **Settings**                                     | **Description**                                                                       |
| ------------------------------------------------ | ------------------------------------------------------------------------------------- |
| `rwuser noauth`                                  | Provides access to the full OID tree without authentication.                          |
| `rwcommunity <community string> <IPv4 address>`  | Provides access to the full OID tree regardless of where the requests were sent from. |
| `rwcommunity6 <community string> <IPv6 address>` | Same access as with `rwcommunity` with the difference of using IPv6.                  |

### Footprinting the Service

```
snmpwalk -v2c -c public 10.129.14.128
```

żeby znaleźć community tu u góry jest public ale mogą być inne to stosujemy onesixty

```
onesixtyone -c /opt/useful/SecLists/Discovery/SNMP/snmp.txt 10.129.14.128
```
