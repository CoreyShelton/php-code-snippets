# Data Sanitization Function(s)

Use the following functions in conjunction with one another to sanitize your data.

***

### PHP Sanitization Code
```php
//Function for stripping out malicious bits
function cleanInput($input) {
    
    $search = array(
        '@<script[^>]*?>.*?</script>@si',   // Strip out javascript
        '@<[\/\!]*?[^<>]*?>@si',            // Strip out HTML tags
        '@<style[^>]*?>.*?</style>@siU',    // Strip style tags properly
        '@<![\s\S]*?--[ \t\n\r]*>@'         // Strip multi-line comments
    );
        
    $output = preg_replace($search, '', $input);
    return $output;
}
    
//Sanitization function
function sanitize($input) {
    if (is_array($input)) {
        foreach($input as $var=>$val) {
            $output[$var] = sanitize($val);
        }
    } else {
        if (get_magic_quotes_gpc()) {
            $input = stripslashes($input);
        }
        $input  = cleanInput($input);
        $output = mysql_real_escape_string($input);
    }
    return $output;
}
```

***

### Use Case

#### HTML
```html 
// Simple form with a first name input field
<form>
    <input type="text" id="first_name" name="first_name" value="" />
    <br/>
    <input type="submit" id="submit" name="submit" />
</form>
```
#### PHP
```php
// Sanitize the input from the 'first_name' form field
$fname = sanitize($_REQUEST['first_name']);
```
