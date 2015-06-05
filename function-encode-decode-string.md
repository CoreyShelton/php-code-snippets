# Encode and Decode Strings

Using the following functions you can encode and decode strings.

***

### PHP
```php
<h3>Encode</h3>
<?php 
$encrypted_string = "How Are You";
$encoded_string = convert_uuencode($encrypted_string);
echo $encoded_string;
?>

<h3>Decode</h3>
<?php 
$decoded_string = convert_uudecode($encoded_string);
echo $decoded_string;
?>
```
