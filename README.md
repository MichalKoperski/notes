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

# info gathering



{% embed url="https://en.wikipedia.org/wiki/WHOIS" %}

```
whois facebook.com
whatweb -a4 10.129.26.63 -v

nslookup facebook.com

dig facebook.com @1.1.1.1

#Querying: A Records for a Subdomain
nslookup -query=A facebook.com
dig a www.facebook.com @1.1.1.1

#Querying: PTR Records for an IP Address
nslookup -query=PTR 31.13.92.36
dig -x 31.13.92.36 @1.1.1.1

#Querying: ANY Existing Records
nslookup -query=ANY facebook.com
dig any google.com @8.8.8.8

#Querying: TXT Records
nslookup -query=TXT facebook.com
dig txt facebook.com @1.1.1.1

#Querying: MX Records
nslookup -query=MX facebook.com
dig mx facebook.com @1.1.1.1
```

**WafW00f**

```
wafw00f -v https://www.tesla.com
```

Identifying Nameservers

```
nslookup -type=NS zonetransfer.me
```

Testing for ANY and AXFR Zone Transfer

```
nslookup -type=any -query=AXFR zonetransfer.me nsztm1.digi.ninja
```

### Gobuster

{% code overflow="wrap" fullWidth="true" %}
```
export TARGET="facebook.com"
export NS="d.ns.facebook.com"
export WORDLIST="numbers.txt"
gobuster dns -q -r "${NS}" -d "${TARGET}" -w "${WORDLIST}" -p ./patterns.txt -o "gobuster_${TARGET}.txt"
```
{% endcode %}

Name-based Virtual Hosting

{% code overflow="wrap" fullWidth="true" %}
```
curl -s http://192.168.10.10
curl -s http://192.168.10.10 -H "Host: randomtarget.com"

#Now we can automate this by using a dictionary file of possible vhost names (such as /opt/useful/SecLists/Discovery/DNS/namelist.txt
cat ./vhosts | while read vhost;do echo "\n********\nFUZZING: ${vhost}\n********";curl -s -I http://192.168.10.10 -H "HOST: ${vhost}.randomtarget.com" | grep "Content-Length: ";done
```
{% endcode %}

vHost Fuzzing

```
ffuf -w ./vhosts -u http://192.168.10.10 -H "HOST: FUZZ.randomtarget.com" -fs 612
```
