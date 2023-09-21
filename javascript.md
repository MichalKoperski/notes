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

# JavaScript

{% code overflow="wrap" fullWidth="true" %}
```javascript
// - znak komentarza

// wyswietlanie tekstu w konsoli

console.log("Tekst sie wyswietli w konsoli");

alert("Tutaj tez wyswietli sie tekst w pop-upie");

prompt("Wpisz swoje imie: ");

// zmienne
var varName;
var varName2 = "string";  // string
var myNumber = 2; // typ: integer
var myFloat = 3.4 ;  // liczba zmiennoprzecionkowa

console.log("To jest liczba zmiennoprzecinkowa: " + myFloat);

var myBool = true ;  // wartosc  boolowska true/false

var myObject = new String();

// okreslenie typu zmiennej

typeof myNumber;

// type casting

var myString = "12345";
var myTypeCasting = Number(myString);
console.log("Zmieniamy typ danych ze stringa na liczbe. Nasza liczba to: ", Number(myString) + " A nasz typ teraz to " + typeof myTypeCasting );

var myNumber2 = 2;
var myTypeCasting2 = String(myNumber2);

console.log("Zmieniamy typ danych ze liczby na stringa. Nasza string to: ", String(myNumber2) + " A nasz typ teraz to " + typeof myTypeCasting2 );



var a = 10 ;
var b = 20 ; 

var addition = a + b ;
var substraction = a - b ;
var multiplication = a * b ;
var division = a / b ;
var modulo = a % b ;
var exponentiation = a ** b; 

console.log(" addition: " + addition + " substraction " + substraction + " multiplication " + multiplication + " division " + division + " modulo " + modulo + " exponentiation " + exponentiation);

// dzialanie na stringach

var firstString = "Lag ";
var secondString = "w glowie";

console.log(firstString + secondString);


// dzialanie na stringach

var firstString = "Lag ";
var secondString = "w glowie";

console.log(firstString + secondString);

// dlugosc stringa
var lengthString = "Kod 200 - OK";
console.log(lengthString.length);

// indexowanie w stringu zaczyna sie od 0 

console.log("Pierwszy znak w stringu: " + lengthString[0]);

console.log("Index dla pierwszego znaku 0 w stringu: " + lengthString.indexOf("0"));

// operacje logiczne

var c= 10;
var d= 5;

var greaterThan = c > d; // true
var lowerThan = c < d;  // false 
var greaterOrEqualThan = c >= d; // true
var lowerOrEqualThan = c <= d; // false
var equal = c == d;  // false
var notEqual = c != d; // true

// if (warunek) {
//     to co sie wykona jesli warunek bedzie spelniony
// }

var num = Number(prompt("Wpisz liczbe: ")); 
var word = prompt("Wpisz slowo: ");
if (num > 13){
    console.log("Liczba jest wieksza od 13"); 
} else if (word == "cyber"){
    console.log("Nasze slowo to cyber");
} else {
    console.log("Zadne nie jest prawdziwe"); 
}




// zaawansowane operacje logiczne

// && - and
// || - or

var num = Number(prompt("Wpisz liczbe: ")); 
var word = prompt("Wpisz slowo: ");
if (num > 13 && word == "cyber"){
    console.log("Liczba jest wieksza od 13 i zgadles nasze slowo"); 
} else if (num <= 13 && word == "cyber"){
    console.log("Liczba jest mniejsza lub rowna od 13 i zgadles nasze slowo");
    } else if (num > 13 || word == "cyber" ) {
        console.log("Zgadza sie warunek z liczba lub trafiles slowo");
    } else {
    console.log("Zadne nie jest prawdziwe"); 
}



var liczba1 = Number(prompt("Podaj pierwszą liczbę: "));
var liczba2 = Number(prompt("Podaj drugą liczbę:"));
if (liczba1 > liczba2){
    var wynik = liczba1 - liczba2
    alert("Wynik odejmowania podanych liczb wynosi: " + wynik);
}
else{
    var wynik2 = liczba2 - liczba1
    alert("Wynik odejmowania podanych liczb wynosi: " + wynik2);
}



// punkt 1 

var num11 = Number(prompt("wpisz pierwsza liczbe: "));
var num12 = Number(prompt("wpisz druga liczbe: "));

alert("wynik to: " + (num11 + num12));

// punkt 2

var num21 = Number(prompt("wpisz pierwsza liczbe: "));
var num22 = Number(prompt("wpisz druga liczbe: "));

if (num21 >= num22){
    alert("wynik: " + (num21 - num22));
}
else {
    alert("wynik: " + (num22 - num21));
}



// var num1 = Number(prompt("Wpisz pierwsza liczbe: ")); 
// var num2 = Number(prompt("Wpisz druga liczbe: ")); 
// var sum = num1 + num2
// alert("Suma podanych liczb to: " + sum);

// if (num1 >= num2){
//     sub = num1 - num2
// } else if (num1 < num2){
//     sub = num2 - num1
// }
// alert("Suma odejmowania wiekszej od mniejszej to: " + sub);

// aktualizacja

// podpunkt 3
var num1 = Number(prompt("Wpisz pierwsza liczbe: ")); 
var num2 = Number(prompt("Wpisz druga liczbe: ")); 
var operation = prompt("Wpisz rodzaj dzialania (/*-+): ");

if (operation == "/" ){
    if (num2!=0) {
        var result = num1/num2;
        alert("wynik dzielenia to: " + (num1/num2))
    } else {
        alert("nie mozna dzielic przez 0!")
    }  
} else if (operation == "*"){
    var result = num1*num2;
    alert("wynik mnozenia to: " + (num1+num2))
} else if (operation == "-"){
    var result = num1-num2;
    alert("wynik odejmowania to: " + (num1-num2))
} else if (operation == "+"){
    var result = num1+num2;
    alert("wynik dodawania to: " + (num1+num2))
} else {
    alert("Nie ma takiego dzialania. Wybierz poprawne dzialanie. (/*-+):");
}
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```html
<!DOCTYPE html> 
<html lang="en"> 
<head> 
‹meta charset="UTF-8">
<meta http-equiv="X-UA-Compatible" content= "IE=edge"> 
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Calculator</title> 
<script src=" /is/calculator.¡s"></script>
</head> <body>

</bodv> </htmls
```
{% endcode %}
