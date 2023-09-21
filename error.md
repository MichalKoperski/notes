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

# error

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (3).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (1).jpg" alt=""><figcaption></figcaption></figure>

</div>

{% code fullWidth="true" %}
```python
try:
  num1=10
  num2="a"
  print(num1/num2)
except Exception as my_error:
  print(f"Działanie jest niedozwolone ponieważ {my_error}")
finally:
  num1=str(num1)
  print(f"{num1}/{num2}")
  
------------------console output
Działanie jest niedozwolone ponieważ usupported operand type(s) for /: 'int' and 'str'
10/a
```
{% endcode %}
