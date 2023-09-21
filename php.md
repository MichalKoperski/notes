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

# php

{% code overflow="wrap" fullWidth="true" %}
```php
Tworzymy dwa pliki w katalogu /htdocs

index.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PHP - basic</title>
</head>
<body>
 
<form action="index.php" method="post">
Liczba 1: <input type="text" name="num1"> <br>
Liczba 2: <input type="text" name="num2">
 <input type="submit" name="submit" value="Submit">
</form>

</body>
</html>

==================================
index.php


<!DOCTYPE html>
<html>
  <head>
<meta charset="UTF-8">
<title>PHP</title>
  </head>

  <body>

<?php
if (empty($_POST['num1']) or empty($_POST['num2']) ){
echo("Pole nie moze byc puste");
}else {
  $num1 = $_POST['num1'];
  $num2 = $_POST['num2'];
  echo($num1 + $num2); 
}

?>


  </body>


</html>
```
{% endcode %}
