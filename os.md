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

# os

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (5).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (3).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/3 (2).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
import os

os.system(r"ifconfig > ifconfig.txt")
my_file=open("ifconfig.txt","r",encoding="latin-1",errors="ignore")

for line in my_file:
  adress=line.replace("\n","")
  if "inet" in string:
    print(adress)
    break
  else:
    continue
```
