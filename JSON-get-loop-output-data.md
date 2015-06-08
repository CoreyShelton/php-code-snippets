# Get, Loop, then Output Data

The following code snippets show how you can use either **cURL** or **```get_file_contents()```** to get JSON data, loop through the data, and then output the data.

***

```php
<!doctype html>
<html>
<head>
<meta charset="UTF-8">
<title>Loop Through & Output Data</title>
</head>

<body>

<?php 
// Set the URL variable
$url = "http://www.atlanticbay.com/wp-json/pages";

/********************
*    Using cURL     *
*********************/

//  Initiate curl
$ch = curl_init();
// Disable SSL verification
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);
// Will return the response, if false it print the response
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
// Set the url
curl_setopt($ch, CURLOPT_URL,$url);
// Execute
$result = curl_exec($ch);
// Closing
curl_close($ch);

// Returns the JSON data as an object
$get_value = json_decode($result);
// Returns the JSON data as an associative array
//$get_value = json_decode($result, true);

// When JSON is returned as an object output it like so
echo 'get_value[0]->ID = ' . $get_value[0]->ID . '<br><br>';

// Print out the variable 
echo '<pre>';
print_r(json_decode($result)); // Output as an object
//print_r(json_decode($result, true)); // Output as associative array
echo '</pre>';

/******************************
*  USING file_get_contents()  *
*******************************/

//get JSON data using either file_get_contents or cURL
$result = file_get_contents($url);

//decode JSON string & convert it into a PHP variable. 
$json_object = json_decode($result);

// Output single value from the 1st array element
echo $json_object[0]->ID . '<br>';
echo $json_object[0]->title . '<br>';

// Loop through the JSON data
for ($x = 0; $x < count($json_object) ; $x++) {
    echo $json_object[$x]->ID . '<br>';
    echo $json_object[$x]->title . '<br>';
}
echo '<hr/>';

// Print out the variable 
echo '<pre>';
print_r($json_object);
echo '</pre>';
?>

</body>
</html>
```
