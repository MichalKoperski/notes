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

# DNS

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>DNS Record</strong></td><td><strong>Description</strong></td></tr><tr><td><code>A</code></td><td>Returns an IPv4 address of the requested domain as a result.</td></tr><tr><td><code>AAAA</code></td><td>Returns an IPv6 address of the requested domain.</td></tr><tr><td><code>MX</code></td><td>Returns the responsible mail servers as a result.</td></tr><tr><td><code>NS</code></td><td>Returns the DNS servers (nameservers) of the domain.</td></tr><tr><td><code>TXT</code></td><td>This record can contain various information. The all-rounder can be used, e.g., to validate the Google Search Console or validate SSL certificates. In addition, SPF and DMARC entries are set to validate mail traffic and protect it from spam.</td></tr><tr><td><code>CNAME</code></td><td>This record serves as an alias. If the domain www.hackthebox.eu should point to the same IP, and we create an A record for one and a CNAME record for the other.</td></tr><tr><td><code>PTR</code></td><td>The PTR record works the other way around (reverse lookup). It converts IP addresses into valid domain names.</td></tr><tr><td><code>SOA</code></td><td>Provides information about the corresponding DNS zone and email address of the administrative contact.</td></tr></tbody></table>

The `SOA` record is located in a domain's zone file and specifies who is responsible for the operation of the domain and how DNS information for the domain is managed.

```
dig soa www.inlanefreight.com
```

&#x20; **Local DNS Configuration**

```
cat /etc/bind/named.conf.local
```

**Zone Files**

```
cat /etc/bind/db.domain.com
```

**Reverse Name Resolution Zone Files**

```
cat /etc/bind/db.10.129.14
```

### Dangerous Settings

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Option</strong></td><td><strong>Description</strong></td></tr><tr><td><code>allow-query</code></td><td>Defines which hosts are allowed to send requests to the DNS server.</td></tr><tr><td><code>allow-recursion</code></td><td>Defines which hosts are allowed to send recursive requests to the DNS server.</td></tr><tr><td><code>allow-transfer</code></td><td>Defines which hosts are allowed to receive zone transfers from the DNS server.</td></tr><tr><td><code>zone-statistics</code></td><td>Collects statistical data of zones.</td></tr></tbody></table>

**DIG - NS Query**

```
dig ns inlanefreight.htb @10.129.14.128
```

**DIG - Version Query**

```
dig CH TXT version.bind 10.129.120.85
```

**DIG - ANY Query**

```
dig any inlanefreight.htb @10.129.14.128
```

**DIG - AXFR Zone Transfer**

```
dig axfr inlanefreight.htb @10.129.14.128
```

**DIG - AXFR Zone Transfer - Internal**

```
dig axfr internal.inlanefreight.htb @10.129.14.128
```

**Subdomain Brute Forcing**

{% code overflow="wrap" fullWidth="true" %}
```
for sub in $(cat /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-110000.txt);do dig $sub.inlanefreight.htb @10.129.14.128 | grep -v ';\|SOA' | sed -r '/^\s*$/d' | grep $sub | tee -a subdomains.txt;done
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```
dnsenum --dnsserver 10.129.14.128 --enum -p 0 -s 0 -o subdomains.txt -f /opt/useful/SecLists/Discovery/DNS/subdomains-top1million-110000.txt inlanefreight.htb
```
{% endcode %}
