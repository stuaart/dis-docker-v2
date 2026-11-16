PHP vs. Python
==============
PHP and Python share a bunch of equivalences that are potentially helpful for students of COMP4039 / COMP3084 if they are simultaneously learning Python and / or already are familiar with it. This file contains various examples of these equivalences based on details of the PHP language that we look at in the lectures.

NOTE: Some of the examples have been borrowed from W3Cschools.

## Links
[PHP Sandbox](https://onlinephp.io)
[Python Sandbox](https://pythonsandbox.com)
[W3Cschools - PHP](https://www.w3schools.com/php/)


## Variables and scope

### PHP - declare some strings (type is implied) and concatenate them
```php
$firstName = "Alice"; 
$lastName = "Johnson"; 
$fullName = $firstName . " " . $lastName;

echo fullName;
```

### Python - pretty much identical to the PHP equivalent
```python
firstName = "Alice"
lastName = "Johnson"
fullName = firstName + " " + lastName

print(fullName)
```

### PHP - testing different variable scopes, i.e., global vs. local
```php
function myFunction() { 
	$localVariable = "World";
	//echo $globalVariable; // Attempting access to the global variable here – this throws an error!
 	$globalVariable = "Changed "; // Locally defining a variable that shares the same name as a global variable; this will work, although it can be confusing :)
 	//global $globalVariable; // Another way to access the global variable from within the function, commented out for now
	
	echo $GLOBALS["globalVariable"] . $localVariable . "\n"; // Or you can access the global variable via supervariables
	echo $globalVariable . $localVariable; // By default this will access the locally-defined variable that happens to share the same name as the global variable (confusing!)
}

$globalVariable = "Hello ";

myFunction();
```

### Python - this is pretty much a straightforward conversion of what you can do in PHP 
```python
def myFunction():
  localVariable = "World"
  #print(globalVariable)
  globalVariable = "Changed "
  #global globalVariable
  print(globals()["globalVariable"] + localVariable)
  print(globalVariable + localVariable)


globalVariable = "Hello "

myFunction()
```

### PHP - static variables persist across calls to a function; probably the most sensible way to use static is in object oriented programming approaches to PHP where you define some static values for a class
```php
function test()
{
    static $a = 0;
    echo $a;
    $a++;
}

test();
echo "\n";
test();
echo "\n";
test();
```

### Python - not really possible to have a direct equivalent, although there is some similar functionality to static variables if we use objects in Python instead
```python
class MyClass:
  a = 0

myclass = MyClass()

def test():
  print(myclass.a)
  myclass.a += 1
  
test()
test();
test();
```

## Operators - virtually identical between PHP and Python with a few exceptions detailed below

### PHP
```php
$a = 15;
$a--;
echo $a."\n";
$a++;
echo $a."\n";

$b = True;
$c = False;
if (!$b)
	echo "logical-not b is true\n";
if ($b && $c)
	echo "b logical-and c is true\n";
if ($b || $c)
	echo "b logical-or c is true\n";
```

### Python 
```python
a = 15
a-=1
print(a)
a+=1
print(a)

b = True
c = False
if not b:
	print("logical-not b is true")
if b and c:
	print("b logical-and c is true")
if b or c:
	print("b logical-or c is true")
```

## Control flow

### PHP - if/elseif/else
```php
$t = date("H");

if ($t < "10") {
  echo "Have a good morning!";
} elseif ($t < "20") {
  echo "Have a good day!";
} else {
  echo "Have a good night!";
}

$favcolor = "red";
```

### Python - note that we have to import functionality whereas for PHP date functions (like many other things) are built in; we also see the way Python has consistency in its syntax regarding classes and ways to call methods on objects even if we are operating in 'procedural' mode within our Python script...
```python
import datetime

t = datetime.datetime.now().strftime("%H")

if t < "10":
  print("Have a good morning!")
elif t < "20":
  print("Have a good day!")
else:
	print("Have a good night!")
```

### PHP - switch. I've removed a "break" to show how the case comparison is only done *once* for the whole switch statement (i.e., matching $favcolor with "red"). After that point the code just executes whatever is next in line, ignoring the subsequent "case" comparisons.
```php
$favcolor = "red";

switch ($favcolor) {
  case "red":
    echo "Your favorite color is red!";
    //break; // NOTE: edited out to demonstrate what happens if we don't do a break after each case
  case "blue":
    echo "Your favorite color is blue!";
    break;
  case "green":
    echo "Your favorite color is green!";
    break;
  default:
    echo "Your favorite color is neither red, blue, nor green!";
}
```

### Python - Python does not have a switch statement, but a "match" instead. Also note that Python treats each case as having an invisible "break".
```python
favcolor = "red"

match favcolor:
  case "red":
    print("Your favorite color is red!")
  case "blue":
    print("Your favorite color is blue!")
  case "green":
    print("Your favorite color is green!")
  case _:
    print("Your favorite color is neither red, blue, nor green!")
```

### PHP - for and foreach loops
```php
for ($x = 0; $x <= 10; $x++) {
  echo "The number is: $x <br>";
}
```

### Python - there is no identical for loop approach to PHP 
```python
for x in range(0, 10):
  print("The number is: ", x, "<br>")
```

### PHP
```php
$members = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

foreach ($members as $key => $value) {
  echo "$key : $value <br>";
}
```

### Python - foreach is just a standard Python "for", although it does not have the laboured syntax found in PHP about separating key/value pairs
```python
members = {"Peter": "35", "Ben": "37", "Joe": "43"}

for key in members:
  print(key + " : " + members[key] + "<br>")
```

### PHP - while / do-while
```php
$i = 1; 
while ($i < 6) {
  echo $i;
  $i++;
}

$i = 1;

do {
  echo $i;
  $i++;
} while ($i < 6);
```

### Python - note that Python has no do-while loop, so one way of achieving the same effect is to use a break condition; note also that while breaks do exist in Python they are not used for switches!
```python
i = 1
while i < 6:
    print(i)
    i += 1

i = 1
while True:
    print(i)
    i += 1
    if not i < 6:
        break
```

## Strings - most string escape characters are the same, although note that Python's print() function adds a newline by default, unlike PHP's echo. You can fix this with the following in Python:
```python
print("My string", end="")
```

### PHP - string contatenation
```php
$a = "hello"; 
$b = " world"; 
echo $a.$b;
```

### Python
```python
a = "hello"
b = " world"
print(a+b)
```

### PHP - various string manipulation functions available in PHP, with some equivalents, just two examples here and not comprehensively covered of course
```php
$a = "My string with words in";
echo strlen($a) . "\n";
echo str_word_count($a) . "\n";
```

### Python
```python
a = "My string with words in"
print(len(a))
print(len(a.split()))
```

## Functions, arguments, return types and getting types 

### PHP - with the following example, if you do not specify argument types then PHP will parse the second argument (a string) as a number, stripping out "days" and retaining the value 5 (you will receive a warning, however)
```php
function add($a, $b) { // replace with add(int $a, int $b) and it will error
	return $a + $b;
}

echo add(5, "5 days") . "\n";
echo gettype("5 days"); // this tells us what type a data structure / variable / object is - in this case a string
```

### Python - you can't really do the same thing with Python, instead it will throw an error about the wrong types being passed into the function, since it infers that the string should be something that works with the + operator working with an integer (e.g., int, float, etc.); however you can simulate it with a list comprehension:
```python
def add(a, b):
	return a + b

print(add(5, [int(n) for n in "5 days".split() if n.isdigit()][0]))
type("5 days")
```

### PHP - we're specifying full types (argument types and return types), which is probably good practice in general unless you want to do type checking in your function with gettype() as illustrated above
```php
function increment(int $x, int $inc = 1) : int {
	return $x + $inc;
}

echo increment(100, 5) . "\n"; // returns 105
echo increment(5) . "\n"; // returns 6
```

### Python -  here we are also using explicit typing ("type hints") to create an equivalent example, however given the Python interpreter's handling of weak typing as compared with that of PHP, it seems unnecessary to do this
```python
def increment(x: int, inc: int = 1) -> int:
	return x + inc

print(increment(100, 5))
print(increment(5))
```

## Arrays - associative arrays are one of the main data structures you will use in PHP, and they closely mirror dictionaries in Python, including the various things you can do with them, including indexing and sorting

### PHP - arrays in PHP are a little bit of a mess; you can only refer to array elements by index if they are made purely from values, with no keys, and in that case the index is counted only for elements with no key... confusing?
```php
$car = array("brand" => "Ford", "model" => "Mustang", "year" => 1964, "USA");

function printVals($array) {
	foreach ($array as $key => $val) {
		echo "$key: $val<br/>\n";
	}
}

printVals($car);
echo "the year is " . array_keys($car)[2] . "\n"; // refer to array values by index
echo "the country of origin is " . $car[0] . "\n"; // elements with *only* values can be indexed directly
asort($car);
printVals($car);
```

### Python
```python
car = {"brand": "Ford", "model": "Mustang", "year": 1964, 0: "USA"}

def printVals(array):
    for key, val in array.items():
        print(f"{key}: {val}<br/>")

printVals(car)
print("the year is " + list(car.keys())[2])
print("the country of origin is " + car[0])

car = dict(sorted(car.items(), key=lambda kv: str(kv[1])))
printVals(car)
```

## Error handling

### PHP - using a try-catch to manage errors instead of just using die() for every error, although sometimes die() may be more appropriate such as in case of really fatal errors. Note that the conditional exposes PHP weirdness. 0 == False in PHP, and 0 == Null in PHP too. PHP also has a "finally" block that is possible, although it is not as extensive as Python's error handling.
```php
function inverse($x) {
	if (!$x) { // 0 == False in PHP! Probably better to check the actual value as in the Python equivalent below
	    throw new Exception('Division by zero.');
	}
	return 1/$x;
}

try {
	echo inverse(5) . "\n";
	echo inverse(0) . "\n";
} catch (Exception $e) {
	echo "Caught exception: ",  $e->getMessage(), "\n";
} // Continue execution

echo "Hello World\n";
```

### Python - exceptions operate on a very similar basis, however we can arbitrarily handle more kinds of exceptions as illustrated below.
```python
def inverse(x):
	if not x: # Python also treats 0 as False, but not None (Python equivalent of Null)
		raise Exception("Division by zero.")
	return 1/x

try:
	print(inverse(5))
	print(inverse(0))
except Exception as err:
	print("Caught exception: ",  repr(err))
except:
	print("Another error occurred")

print("Hello World")
```