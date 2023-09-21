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

# log parsing

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (6).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
import os

os.system(r"ping -n 20 8.8.8.8 > ping_log")
ping_log = open("ping_log","r")
for line in ping_log:
  new_line=line.replace("\n","")
  if "bytes" in line and "time" in line:
    list=new_line.split(" ")
    if float(list[4].replace("time=","").replace("ms",""))<21;
      print(f"Bajty {list[3]} i {list[4]}")
  else:
    continue
```
