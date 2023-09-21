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

# NETWORKING &#x20;



```
ping <remote_host>

traceroute www.inlanefreight.com

netstat -a
```

<div data-full-width="true">

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

</div>

<table data-header-hidden data-full-width="true"><thead><tr><th></th><th></th></tr></thead><tbody><tr><td><strong>Layer</strong></td><td><strong>Function</strong></td></tr><tr><td><code>7.Application</code></td><td>Among other things, this layer controls the input and output of data and provides the application functions.</td></tr><tr><td><code>6.Presentation</code></td><td>The presentation layer's task is to transfer the system-dependent presentation of data into a form independent of the application.</td></tr><tr><td><code>5.Session</code></td><td>The session layer controls the logical connection between two systems and prevents, for example, connection breakdowns or other problems.</td></tr><tr><td><code>4.Transport</code></td><td>Layer 4 is used for end-to-end control of the transferred data. The Transport Layer can detect and avoid congestion situations and segment data streams.</td></tr><tr><td><code>3.Network</code></td><td>On the networking layer, connections are established in circuit-switched networks, and data packets are forwarded in packet-switched networks. Data is transmitted over the entire network from the sender to the receiver.</td></tr><tr><td><code>2.Data Link</code></td><td>The central task of layer 2 is to enable reliable and error-free transmissions on the respective medium. For this purpose, the bitstreams from layer 1 are divided into blocks or frames.</td></tr><tr><td><code>1.Physical</code></td><td>The transmission techniques used are, for example, electrical signals, optical signals, or electromagnetic waves. Through layer 1, the transmission takes place on wired or wireless transmission lines.</td></tr></tbody></table>

