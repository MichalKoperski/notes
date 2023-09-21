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

# XSS - htmlentities

{% code fullWidth="true" %}
```php
<html>
<body>

<form method="get" action="<?php echo $_SERVER['PHP_SELF'];?>">
  GET: <input type="text" name="cmd">
  <input type="submit">
</form>

<form method="post" action="<?php echo $_SERVER['PHP_SELF'];?>">
  POST: <input type="text" name="cmd">
  <input type="submit">
</form>

<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $cmd = $_POST['cmd'];

  
    echo "Uzyles metody POST do wyslania ".$cmd;
    echo "<br>".$cmd;
  }
  
  if (($_SERVER["REQUEST_METHOD"] == "GET") && isset($_GET['cmd'])) {
      $cmd = htmlentities($_GET['cmd']);

        echo "Uzyles metody GET do wyslania ".$cmd;
}


?>

</body>
</html>
```
{% endcode %}

<div data-full-width="true">

<figure><img src=".gitbook/assets/1 (21).jpg" alt=""><figcaption></figcaption></figure>

</div>
