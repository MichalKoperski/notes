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

# module

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (2).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
import datetime

def time():
  h=datetime.datetime.today()
  print(f"Godzina {h.hour} minuta: {h.minute}")
  
time()
```

```python
import random

counter = 0
randomNumber = 0

def define_random_num():
    global randomNumber
    randomNumber = random.randint(1,100)

def check_user_num(userPrediction):
    global counter, randomNumber

    counter += 1
    if userPrediction == randomNumber:
        print("Brawo zgadłeś!")
        return True
    elif abs(randomNumber - userPrediction) < 5:
        print("Gorąco!")
    elif abs(randomNumber - userPrediction) < 10:
        print("Ciepło!")
    elif abs(randomNumber - userPrediction) < 20:
        print("Letnio!")
    elif abs(randomNumber - userPrediction) < 40:
        print("Zimno!")
    else:
        print("Bardzo zimno!")
    return False

def main():
    print("Witaj")
    print("Wylosowana liczba jest z zakersu od 1 do 100")

    define_random_num()
    is_find = False
    while not is_find:
        user_input = int(input("Podaj liczbę: "))
        is_find = check_user_num(user_input)
    print(f"Zdagłeś w {counter} prób")

if __name__ == "__main__":
    main()

---------------------console output
Witaj
Wylosowana liczba jest z zakresu od 1 do 100
Podaj liczbę: 44
Zimno!
...
```
