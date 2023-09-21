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

# file permission

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (4).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (2).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/3 (1).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/4 (2).jpg" alt=""><figcaption></figcaption></figure>

</div>

\#tworzymy tekst.txt

Adam

Ewa

Jan

Zbigniew

asdf

123456

```python
try:
  my_file=open(r"tekst","r+")
  print(my_file.read())
  my_file=open(r"tekst","a+")
  my_file.write("\nNowa linijka")
  my_file=open(r"tekst","r")
  print(my_file.read())
except Exception as e:
  print(f"Pojawił się błąd {e}")
```
