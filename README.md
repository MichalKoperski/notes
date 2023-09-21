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

# fundamentals

{% code overflow="wrap" fullWidth="true" %}
```python
#pyta o wiek, ale zmienna age to string
age = input("Podaj wiek: ")

#teraz zmienna age to integer
age = int(input("Podaj wiek: "))

#po if :
if age >= 18:

#pobranie zmiennych i wyświetlenie
num1 = int(input("Podaj liczbę: "))
num2 = int(input("Podaj liczbę: "))

if num1 == num2:
  print(num1," jest równe ", num2)
elif num1 > num2:
  print(f"{num1} jest większe od {num2}")
else:
  print(f"{num1} jest mniejsze od {num2}")
  
#weryfikacja wartości stringa - w ""
if action == "+"

#weryfikacja dwóch warunków na raz
if action == "/" and num2 != 0:

#zbiór, array którego nie można modyfikować
tuple = (1,2,3,"aaa")

#wyświetlanie w dwóch liniach
print(tuple1, "\n", tuple2)

#wyświetli oba zbiory
print(tuple1 + tuple2)

#array którą można modyfikować i wyciągać pojedyncze
list = ["opel","BMW"]

#opel
list[0]

#kasowanie BMW
del list[1]

#dodawanie
list.append("VW")

#kasowanie
list.remove("VW")

#słownik czyli mapa - klucz:wartość
mydiction={"name":"David","age":24}

#kasowanie po kluczu
del mydiction["age"]
#i zostanie tylko name David

#updatowanie wartości age
mydiction["age"]=80
#i wiek się zmieni z 24 na 80

#wylistowanie kluczy
print(mydiction.keys())

#dodanie nowego duetu klucz:wartość
mydiction.update({"height":184})

#w string też możemy odwołać się do danej litery
a = michal

#i to będzie
a[1]

#przekopiowanie podzielonego textu spacjami do listy b
a = "jest super"
b = a.split(" ")
print(b) 
#wyświetli ["jest", "super"]
```
{% endcode %}
