# PHP

---

## VARIABLES

```php
    $myVariable = 30

    define('MYCONSTANT', 'Hello')
```

---

## STRINGS

With " ", can use variable directly in the string. Ex:

```php
    "Hello $myVariable"
```

With ' ', we have to concatenate it.

#### Concatenation

Concatenate with a dott.

```php
    'Hello ' . 'World' --> 'Hello World'
```

#### Escaping

```php
    "The ninja said \"wahhh\" !!!"
```

#### Index

```php
    $name = "Henrique"
    $name[2] === "n"
```

#### String functions (methods)

```php
    $name = 'Henrique'

    strlen($name) === 8

    strtoupper($name) === 'HENRIQUE'

    strtolower($name) === 'henrique'

    str_replace('e', 'w', $name) === 'Hwnriquw'
```

---

## NUMBERS

#### Basic operators

+| - | \* | / | \*\*(power)

#### Shorthand operators

```php
    $number = 5

    $number++   === 6

    $number--   === 4

    $number+=10 === 15

    $number-=10 === -5

    $number *=5 === 25
```

#### Number functions (methods)

```php
    $number = 5.3

    floor($number) === 5

    ceil($number) === 6

    pi() === 3.141592....
```

---

## ARRAYS

#### Indexed arrays

```php
// Create array
$myArray = ['element 0', 'element 1', 'element 2'];
or :
$myArray = array('element 0', 'element 1', 'element 2')

// Access array element
$myArray[1] === 'element 1'

// print readable
print_r($myArray)

// Adds new element onto the END
$myArray[] = 'new element'

// Other way to create new element at the end
array_push($myArray, 'new element')

// Remove last element of an array and the return the removed element
array_pop($myArray)

// Count the number of elements in an array
count(myArray)

// Merge two arrays
$arrayOne = ['Henrique', 'Lillie']
$arrayTwo = ['Pedro', 'Mariana']

$mergedArray = array_merge($arrayOne, $arrayTwo) ===
['Henrique', 'Lillie', 'Pedro', 'Mariana']
```

#### Associative arrays

```php
$myAssociativeArray = ['profession'=>'webdev','age'=>33, 'name'=>'Henrique']
or
$myAssociativeArray = array('profession'=>'webdev', 'age'=>33)

$myAssociativeArray['age'] === 33

// Create new key/value pair in the array
$myAssociativeArray['newKey'] = 'newValue';

// Merge works the same way
array_merge($arrayOne, $arrayTwo)
```

#### Multidimentional arrays

Arrays within arrays. (arrays as elements of an array)

```php
$multidimentional = [
    [1,2,3],
    [4,5,6],
    [7,8,9]
]

$multidimentional[1][2] === 6
```

Works with associatives array as well

```php
$posts = [
    ['title'=>'Hello', 'author'=>'henrique', 'content'=>'lorem'],
    ['title'=>'Goodbye', 'author'=>'Lillie', 'content'=>'lorem'],
    ['title'=>'Oh Yeah!', 'author'=>'Pedro', 'content'=>'lorem']
];

$posts[1]['author'] === 'Lillie'

// Add a new entry
$posts[] = ['title'=>'Uhuuu', 'author'=>'Mariana', 'content'=>'lorem']
```

#### Array methods

```php
    array_merge($arrayOne, $arrayTwo);

    array_intersect($arrayOne, $arrayTwo);

    array_filter($array)
    // Will take a callback function. If there is no call back function, it still loops through the array and return true or false from the values of the array.




```

---

## LOOPS

#### for loops

```php
    for ($i=0 ; $i<5 ; i++){

    }
```

#### foreach

```php
    $numbers = [1,2,3,4,5]

    foreach($numbers as $num) {

    }
```

#### while

```php
    $i = 0;

    while($i < count($products)) {
        echo $products[$i]
        $i++
    };
```

---

## BOOLEANS AND COMPARISONS

TRUE returns a string of "1"

FALSE returns an empty string ""

Comparing two strings will evaluate the first letter being precedent.

---

## CONDITIONAL STATEMENTS

```php
$price = 30;

if ($price < 50 && $price > 10 || $price === 24) {
    // DO SOMETHING
} elseif {
    // DO ANOTHER THING
} else {
    // DO SOMETHING ELSE
}
```

```php
    switch ($weather) {
        case "rain":
            echo "take an umbrella";
            break;
        case 'storm':
            echo "Don't get out today!";
            break;
	    default:
		    echo "Weather will be ok to day";
    }
```

---

## CONTINUE and BREAK

BREAK breaks the loop in a condition.

CONTINUE skips the iteration in a condition.

---

## FUNCTIONS

```php
// DECLARE THE FUNCTION
    function myFunction($name = 'default'){
        echo 'Goodmorning, '.$name
        return // something
    }

// CALL THE FUNCTION

    myFunction('Henrique)
```

---

## VARIABLE SCOPE

To use a global variable inside a scope, we must call the GLOBAL syntaxe.

```php
$age = 33;

function myFunc(){
    /* Must declare the variable inside the scope
    and has to be set as global to take the value from outside */
    global $age
    echo $age
}
```

## must review variable by reference

---

## INCLUDE and REQUIRE

#### INCLUDE

Includes another php file to be ran at this point. If the file is absent, the code follows along.

#### REQUIRE

Does the same thing. But breaks the code if it doesn't encounter the required code.

---

## FORMS

Prevent XSS :

htmlspecialchars()

```php
    htmlspecialchars($_POST['email'])
```

#### Basic Form Validation

```php
if(empty($_POST['email'])) {
    echo "An email is required"
}
```

filter_var --> Function that returns TRUE or FALSE

FILTER_VALIDATE_EMAIL --> Built-in argument of the function.

```php
$email = $_POST['email'];

if (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
    echo "Not a valid email"
}
```

REGEX

```php
if (preg_match(REGEX, $email))
```

REDIRECT

```php
header("Location: index.php")
```
