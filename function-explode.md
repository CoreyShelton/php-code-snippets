# PHP explode() Function

Explodes or breaks a string into an array. We can easily understand the functionality of this function by the name “explode”. explode() has three parameters, first 2 are required and third is optional.

#### Syntax
```php
explode(string_separator, $str, limit);
```

#### Reference
http://php.net/manual/en/function.explode.php

***

### Example 1 - Code
```php
<?php
$mystr = "Hello Dear, How are you";

// Create an array based on spaces
$array = explode(" ", $mystr);

print_r($array);
?>
```

### Example 1 - Output
```
Array
(
    [0] => Hello
    [1] => Dear,
    [2] => How
    [3] => are
    [4] => you
)
```

***

### Example 2 - Code
```php
<?php
$mystr2 = "one,two,three,four,five,six";

// Create an array based on commas
$array = explode(",", $mystr2);

print_r($array);
?>
```

### Example 2 - Output
```
Array
(
    [0] => one
    [1] => two
    [2] => three
    [3] => four
    [4] => five
    [5] => six
)
```

***

Ref: http://php.net/manual/en/function.explode.php
