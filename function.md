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

# function

<div data-full-width="true">

<figure><img src=".gitbook/assets/1.jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2.jpg" alt=""><figcaption></figcaption></figure>

</div>

{% code fullWidth="true" %}
```python
def my_first_func():
  while true:
    word=input("Podaj slowo: ")
      if word=="exit":
        break
    print(f"{word}ish")
    
def my_first_return(word):
  return word+"ish"
  
print(my_first_return("nowe"))
```
{% endcode %}

{% code fullWidth="true" %}
```python
new_word=lambda x,y: x+y
print(new_word("asd","f"))
```
{% endcode %}

<div data-full-width="true">

<figure><img src=".gitbook/assets/3.jpg" alt=""><figcaption></figcaption></figure>

</div>

{% code fullWidth="true" %}
```python
def calc(a,b):
  if type(a)==type(1) and type(b)==type(1):
    return 2*a+2*b
  else:
    return 0

def simple_calc(a,b):
  sum=0
  a=2*a
  b=2*b
  sum=a+b
  return sum

print(calc(1,2))
```
{% endcode %}

{% code fullWidth="true" %}
```python
def list_calc(a):
  sum=0
  for i in a:
    sum+=i*2
  return sum
  
print(list_calc([1,2,3,4,5]))
```
{% endcode %}

<div data-full-width="true">

<figure><img src=".gitbook/assets/4 (1).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/5 (1).jpg" alt=""><figcaption></figcaption></figure>

</div>

{% code fullWidth="true" %}
```python
db={"Admin":"Admin", "admin":"pass","Ewa":"123","Adam":"asdf"}

def auth(user,passwors):
  if user in db.keys() and password in db[user]:
    print("Jesteś zalogowany")
    return true
  else:
    print("błędne dane")
    return false
    
username =input("Podaj username: ")
password=input("Podaj haslo: ")

auth(username,password)
```
{% endcode %}

<div data-full-width="false">

<figure><img src=".gitbook/assets/6 (1).jpg" alt=""><figcaption></figcaption></figure>

</div>

<figure><img src=".gitbook/assets/7 (1).jpg" alt=""><figcaption></figcaption></figure>

```python
var_one=18

def tmp():
  var_one=19
  var_one=var_one+30
  return var_one
  
print(var_one)
print(tmp)
print(var_one)

----------------------cosole output
18
49
18
```

**global**

```python
var_one=18

def tmp():
  global var_one
  var_one=var_one+30
  return var_one
  
print(var_one)
print(tmp)
print(var_one)

----------------------cosole output
18
48
48
```

```python
counter=0

def key_log():
  global counter
  counter=0
  keys_count=len(input("Podaj hasło: "))
  counter+=keys_count
  return keys_count
  
print(key_log())
print(counter)

--------------------console output
Podaj hasło: 123456
6
6
```

```python
counter=0

def key_log():
  global counter
  counter=0
  keys_count=len(input("Podaj hasło: "))
  counter+=keys_count
  return keys_count
  
while true:
  print(key_log())
  print(counter)

--------------------console output
Podaj hasło: 123456
6
6
Podaj hasło: 12
2
2
Poda...
```

**kasujemy zerowanie countera w funkcji**

```python
counter=0

def key_log():
  global counter
  keys_count=len(input("Podaj hasło: "))
  counter+=keys_count
  return keys_count
  
while true:
  print(key_log())
  print(counter)

--------------------console output
Podaj hasło: 12
2
2
Podaj hasło: 1234
4
6
Podaj hasło: 123456
6
12
```
