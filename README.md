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

# burp suite

<div data-full-width="true">

<figure><img src=".gitbook/assets/1.jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2.jpg" alt=""><figcaption></figcaption></figure>

</div>

wchodzimy na [http://burp](http://burp) i ściągamy CA Certificate

<figure><img src=".gitbook/assets/1 (1).jpg" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/2 (1).jpg" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/3.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/4.jpg" alt=""><figcaption></figcaption></figure>

i importujemy

<figure><img src=".gitbook/assets/1 (2).jpg" alt=""><figcaption></figcaption></figure>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (2).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/3 (1).jpg" alt=""><figcaption></figcaption></figure>

</div>

**TRAFFIC INTERCEPTION & MANIPULATION**

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (3).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (3).jpg" alt=""><figcaption></figcaption></figure>

</div>

**REPEATER**

jeśli chcemy zmieniać coś w locie

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (4).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (4).jpg" alt=""><figcaption></figcaption></figure>

</div>

klikamy send i otrzymujemy od razu odpowiedź w sekcji Response

**INTRUDER**

Do robienia brute-force na stronie

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (5).jpg" alt=""><figcaption></figcaption></figure>

</div>

Klikamy Clear §

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (6).jpg" alt=""><figcaption></figcaption></figure>

</div>

i zaznaczamy konkretny parametr, który chcemy fuzzować/brute-forcować i klikamy Add §

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (7).jpg" alt=""><figcaption></figcaption></figure>

</div>

przechodzimy do Payloads

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (8).jpg" alt=""><figcaption></figcaption></figure>

</div>

i wybieramy payload type

a w payload options robimy swoją listę do payload, czyli jakie wartości mają być zaczytane w miejsce zaznaczone §§

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (9).jpg" alt=""><figcaption></figcaption></figure>

</div>

i klikamy Start Attack

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (10).jpg" alt=""><figcaption></figcaption></figure>

</div>

_TYPY ATAKÓW_

SNIPER

Po jednym payloadzie na raz

BATTERING RAM

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (11).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (5).jpg" alt=""><figcaption></figcaption></figure>

</div>

strzelamy jednocześnie w kilka miejsc

jednocześnie w USER i PHPSESSID

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (12).jpg" alt=""><figcaption></figcaption></figure>

</div>

PITCHFORK

korzysta z kilku setów payload

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (13).jpg" alt=""><figcaption></figcaption></figure>

</div>

mamy do wyboru 2 zestawy payload

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (14).jpg" alt=""><figcaption></figcaption></figure>

</div>

Payload 1 będzie umieszcany gdzie jest 1 pozycja - tam gdzie §bee§

payload 2 tam gdzie 2 pozycja - §bug1212§

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (15).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (6).jpg" alt=""><figcaption></figcaption></figure>

</div>

ogólna lista payloadów będzie równa najkrótszej liście z tych payload

1 attak - 1 wartość z payload set 1 i 1 wartość z payload set 2 - czyli w parach

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (16).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (7).jpg" alt=""><figcaption></figcaption></figure>

</div>

CLUSTER BOMB

tak jak pitchfork, tylku tu robi wszystki kombinacje payload set 1 z każdym wpisem z payload set 2 itd

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (17).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (8).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/3 (2).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/4 (1).jpg" alt=""><figcaption></figcaption></figure>

</div>

**SEQUENCER**

próbuje znaleźć sposób generowania niby losowych np. sesji numerów odpowiedzi jaki jest algorytm/klucz generowania tych liczb przez serwer

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (18).jpg" alt=""><figcaption></figcaption></figure>

</div>

**DECODER**

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (19).jpg" alt=""><figcaption></figcaption></figure>

</div>

**COMPARER**

wysyłamy dwa request i porównujemy

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (20).jpg" alt=""><figcaption></figcaption></figure>

</div>

<div data-full-width="true">

<figure><img src=".gitbook/assets/2 (9).jpg" alt=""><figcaption></figcaption></figure>

</div>
