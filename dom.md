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

# DOM

{% code overflow="wrap" fullWidth="true" %}
```
W KONSOLI 

var wstepDiv = document.querySelector('#wstep');
wstepDiv;
var naglowek1 = document.getElementById("naglowek1");
naglowek1

wstepDiv.innerHTML = "<p>Dodalismy paragraaf przy pomocy JS do diva</p>"

1. Tworzymy plik dom.js 

2. Podpinamy go do index.html
- Tag 
<script src="../js/dom.js"></script> uemieszczamy na samym końcu index.html w tagu <body> 

dom.js

var wstepDiv = document.querySelector('#wstep');
console.log(wstepDiv);
wstepDiv.innerHTML = "<p>Dodalismy paragraaf przy pomocy JS do diva</p>";

wstepDiv.setAttribute("align","center");
wstepDiv.style.background = "red";   
lub
wstepDiv.style.color = "red";

w pliku index.html dodajemu id="home"
    
  
<li id="home" class="menu"><a href="index.html">Home</a></li>
            <li class="menu"><a href="formularz.html">Kontakt</a></li>
  

 <li id="kontakt" class="menu"><a href="formularz.html">Kontakt</a></li>

W ty mmomencie dodamy obiekt 


            <li id="home" class="menu"><a href="index.html" id="homeLink">Home</a></li>
            <li id="kontakt" class="menu"><a href="formularz.html" id="kontaktLink">Kontakt</a></li>


dom.js

let text = document.getElementById("homeLink");
document.getElementById("kontaktLink").innerHTML = text;

<button id="btn1">Przycisk pierwszy</button>
<button id="btn2">Przycisk drugi</button>




let text2 = document.getElementById("btn1").innerHTML;
document.getElementById("p1").innerHTML = text2;

index.html

<button id="btn1" onclick="alert('To jest XSS');">Przycisk pierwszy</button>

<button id="btn2" onclick="var btn= document.getElementById('btn2'); btn.innerHTML='<p>Paragraf dodany po kliknieciu przycisku</p>' " >Przycisk drugi</button>
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```html
=========== LABORATORUM - DOM ====================

lab-dom.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DOM - lab</title>
</head>
<body>
    <div id="lab-dom"></div>

<script>
   var element = document.getElementById("lab-dom") ;
   var newParagraph = document.createElement("p");
   var paragraphContent = document.createTextNode("Hello"); 
    newParagraph.appendChild(paragraphContent);
    newParagraph.style.color="blue";
    // element.appendChild(newParagraph);

    var image1 = document.createElement("img");
    image1.src = "https://hackeru.pl/wp-content/uploads/2021/10/logo.png";
    // image1.setAttribute("onclick", "element.appendChild(newParagraph)");
    image1.setAttribute("onmouseover", "element.appendChild(newParagraph)");
    image1.setAttribute("width", "20%");
    element.appendChild(image1);


</script>

</body>
</html>
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```html
======================

advanced-js.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced JS</title>
    <script src="../js/advanced-js.js"></script>
</head>
<body>
    
</body>
</html>

============

advanced-js.js


// funkcje

// funkcje bez parametru 
function konkatenacjaStringow(){
    var str1 = "wywolana";
    var str2 = "funkcja"; 
    console.log(str1 + " " +  str2);
}

// wywolanie funkcji 

konkatenacjaStringow();

// funkcje z parametrem 

function funkcjaZParametrami(parametr1, parametr2){
    var num1 = Number(parametr1);
    var num2 = Number(parametr2);
    var suma = num1 + num2; 
    console.log(suma);
}

//wywolanie funkcji z parametrami 

funkcjaZParametrami(2,10);
funkcjaZParametrami(-2,10);
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```html
============ SILNIA ==============

function silnia(name, number){
    alert("Witaj " + name + ", to jest program do obliczania silni. ");
    var result = 1;
    var numberTypeCasting = Number(number);
    if (numberTypeCasting > 1){
    while (numberTypeCasting > 1){     
        result = numberTypeCasting*result;
        numberTypeCasting -= 1;
    }
    console.log("Silnia podanej liczby wynosi " + result);
    } else {
    console.log("Silnia liczby "+ number +" wynosi 1");
    }
}

silnia(prompt("Wpisz swoje imie " ), prompt("wpisz liczbe: "));


============ LABORATORIUM FUNCTIONS =============

lab-funcitons.html

•	<!DOCTYPE html>
•	<html lang="en">
•	<head>
•	    <meta charset="UTF-8">
•	    <meta http-equiv="X-UA-Compatible" content="IE=edge">
•	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
•	    <title>Lab Funcitons</title>
•	    <script src="../js/lab-funcitons.js"></script>
•	</head>
•	<body>
•	    
•	</body>
•	</html>

lab-funcitons.js  - WYDMUSZKA

// 3 marki samochodow

function clientCar(model){
// jesli to bedzie fiat, to ma kosztowac iles tam, w przeciwnym wypadku, ma kosztowac iles tam 

}

function clientAge(age){
// jesli uzytkownik jest w wieku od > 16 <21 to ma dodatkowo kosztowac tyle, w przeciwnym wypadku naprawa ma kosztowac inaczej

}

function main(){
    // poprosic usera o wybor marki
    // poprosic usera o podanie wieku 
    // policzyc sumaryczna kwote w zaleznosci od odpowiedzi usera
    // uwzgledniamy wyjatki takie jak: brak modelu, podanie wieku ponizej 16 lat i powyzej 21 lat
    // zwrocic uzytkownikowi informacje o kwocie do zaplaty

}

main();

lab-funcitons.js



/
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```html
// 3 marki samochodow

function clientCar(carManufacturer){
if (carManufacturer == 1){
    return 500;}
    else if (carManufacturer == 2){
        return 750;}
        else if (carManufacturer == 3){
            return 1000;}
            else {
                return -1;
            }
}

function clientAge(age){
// jesli uzytkownik jest w wieku od > 16 <21 to ma dodatkowo kosztowac tyle, w przeciwnym wypadku naprawa ma kosztowac inaczej
    if (age < 21 && age >=16){
        return 300; 
    } else if (age >=21) {
        return 100; 
    } else {
        return -1; 
    }

}

function main(){
    // poprosic usera o wybor marki
    // poprosic usera o podanie wieku 
    // policzyc sumaryczna kwote w zaleznosci od odpowiedzi usera
    // uwzgledniamy wyjatki takie jak: brak modelu, podanie wieku ponizej 16 lat i powyzej 21 lat
    // zwrocic uzytkownikowi informacje o kwocie do zaplaty

    var price = 0; 
    var carManufacturer = Number(prompt("Wybierz marke swojego samochodu:\n(1) Fiat, \n(2) Honda, \n(3)BMW"));
    var userAge = Number(prompt("Podaj swoj wiek: ")); 

    var clientAgePrice = clientAge(userAge);
    var clientModelPrice = clientCar(carManufacturer); 
    if (clientAgePrice > 0 && clientModelPrice > 0 ){
        price += clientAgePrice + clientModelPrice; 
        alert("Kwota naprawy wynosi: " + price + "zl. ") 
    } else if (clientAgePrice < 0) {
        alert("Jestes za mlody! Nie moge Cie obsluzyc. ");
    } else if (clientModelPrice < 0){
        alert("Nie ma takiego modelu");
    }

}

main();
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```html
//  Tablice 

var jedenTypDanych = [1,2,3,4,5,6];
var mixDanych = [1,2,"string", "cyber"];
var emptyArray = [];

// odwolanie sie do konkretnego elementu tablicy -> indeksowanie od 0

var odwolanieDoElementu = mixDanych[2];   // string

var dodawanieElementu = mixDanych[4] = "nowy element tablicy na koncu tablicy";

var dodawanieElementuNaKoncuTablicy = mixDanych.push("Ta wartosc bedzie na koncu tablicy");

var dodawanieElementuNaPoczatkuTablicy = mixDanych.unshift(1000);

var usuniecieOstatniegoElementu = mixDanych.pop();

var usunieciePierwszegoElementu = mixDanych.shift();

////  usuniecie dowolnego elementu z tablicy 

var myArray = [1,2,"string", "tablica"];
// splice usuwa dowolny element,  pierwszy arguement to indeks usuwnaego elementu, drugi argument, to ile elementow od tego elementu chcemy usunac. 
var usunietyElement = myArray.splice(2,1);

// PETLE 

// for rosnaco

// for (i=1; i < 10; i++) {
//     console.log(i);
// }

// z przerwaniem iteracji 

for (i=1; i < 10; i++) {
    console.log(i);
    if (i==4){
        console.log("przerwanie petli w iteracji 4");
        break;
    } 
}

// for malejaco 

for (i=10; i > 1; i--) {
    console.log(i);
    if (i==4){
        console.log("przerwanie petli w iteracji 7");
        break;
    } 
}
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```html
// petla WHILE 

var num = 0;

while (1==1) {
    if (num == 3 ){
        console.log("Przerwanie na trzeciej iteracji");
        break;
    }
    console.log("petla: " + num);
    num += 1;
}

var num2 = 0
while (true) {
    if (num2 == 2 ){
        console.log("Przerwanie na drugiej iteracji");
        break;
    }
    console.log("petla: " + num2);
    num2 += 1;
}


lab-arraysAndloops.html






lab-arraysAndloops.js

function addElement(arr) { //arr - array
    add = prompt("Wpisz, co chcesz dodac: ");
    arr.push(add);
}

function removeElement(arr) {
    removeElement2 = prompt("Wpisz, co chcesz usunac: "); 
    // indeksowanie w tablicy jest od zera, wiec jak user poda 1 element, to index dla tego elementu jest 0, wiec musimy od 1 odjac 1
    rem = removeElement2 - 1; 
    arr.splice(rem,1);
}

function displayElement(arr) {
    alert("Obecna tablica: \n" + arr);
}

function main(){
var array = [];
while (options != 4){
    var options = Number(prompt("Witaj, co chcesz teraz zrobic?\nnacisnij (1) - dodaj element\nnacisnij (2) - usun element\nnacisnij (3) - pokaz obecna tablice \nnacisnij (4) - wyjdz z programu"));
    if (options == 1){
            addElement(array);
        } else if (options == 2) {
            removeElement(array);
        } else if (options == 3){
            displayElement(array);
        } else if (options == 4){
            break;
    } else { (alert("Dokonales nieprawidlowego wyboru"));}

}
 
}


main();
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```html
const times = (x,y) => x*y;
function spendTimesWhitBuddies(actions){
    console.log("Czesc wszystkim!");
    actions();
    console.log("Widzimy sie jutro");
}
spendTimesWhitBuddies(() => console.log("Idziemy na pizze!"));
https://kt.academy/pl/article/js-funkcje-strzalkowe
selfExecution.js
window.onload = function(){
    console.log("Strona sie zaladowala;");
}

https://kt.academy/pl/article/js-funkcje-strzalkowe
selfExecution.js
window.onload = function(){
    console.log("Strona sie zaladowala;");
}

📒 https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage

localStorage.setItem('mojZawod','Pentester');
```
{% endcode %}
