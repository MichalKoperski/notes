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

# nosql

{% code overflow="wrap" fullWidth="true" %}
```sql
# Instalacja MONGO v5.0:
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/5.0 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
sudo apt-get update
sudo apt-get install gnupg
sudo apt-get install -y mongodb-org
sudo service mongod start
mongo (jak nie zadziała to: sudo apt install mongodb-clients)
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```sql
show dbs
use Nazwa_bazy
use hacks

#wyswietla nazwę bazy na której operujemy
db

db.createCollection("Nowa_kolekcja")
#UWAGA Case sensitive!! w przeciwieństwie do mysql
db.createCollection("hackers")

#Wyświetla kolekcje
show collections

db.NAZWA-KOLEKCJII.insertOne({ name:"John",surname:"Doe",age:21})
db.hackers.insertOne({ name:"Troy",surname:"Hunt",age:40})
db.hackers.insertOne({ name:"Kevin",surname:"Mittnick",age:56})

db.hackers.find()
db.hackers.find({surname:"Mittnick"})

#Usuwanie danych
db.NAZWA-KOLEKCJII.remove({ age:21 })
db.hackers.remove({age:40})

#Usuwanie całej kolekcji
db.<nazwa-kolekcji>.drop()
db.hackers.drop()
show collections

db.dropDatabase()
dbs

#czytelniejsze wyświetlanie
db.hackers.find().pretty()

db.hackers.insertMany([{name:"haxor",surname:"Hakerski", age:21},{name:"game",surname:"over", age:99}])
db.hackers.find({surname:"over"})

db.users.find({name:{"$regex":"D*"}})

username[$regex]=^J...&password[$exists]
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```sql
#tworzenie admina
db.createUser({ user: "mongoadmin" , pwd: "mongoadmin", roles: ["userAdminAnyDatabase", "dbAdminAnyDatabase", "readWriteAnyDatabase"]})

#plik konfiguracyjny: /etc/mongod.conf
setParameter:
  enableLocalhostAuthBypass: false
security:
  authorization: enabled
```
{% endcode %}

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (23).jpg" alt=""><figcaption></figcaption></figure>

</div>

```python
#wylistowanie wszystkich pozycji które mają usera i password
127.0.0.1/data.php?username[$exists]=&password[$exists]=
```
