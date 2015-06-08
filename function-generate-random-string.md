# Generate a Randome String

The following code snippet creates a random 10 character string.

***

```php
<?php
function genRndString($length = 10, $chars = '1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ!@#$') {
    if($length > 0) {
        
        $len_chars = (strlen($chars) - 1);
        $the_chars = $chars{rand(0, $len_chars)};
        
        for ($i = 1; $i < $length; $i = strlen($the_chars)) {
            $r = $chars{rand(0, $len_chars)};
            if ($r != $the_chars{$i - 1}) $the_chars .=  $r;
        }

        return $the_chars;
    }
}

$str = genRndString();

echo $str . '<br>';
?>
```

***

#### Reference
URL: http://www.sanwebe.com/2011/01/generate-random-string-using-php
