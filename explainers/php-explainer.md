# COMP4039: PHP examples from lecture - try these examples with https://onlinephp.io


## The basics
```html
<html>
	<body>
		<?php
			echo "<h1>Hello World!</h1>";
		?>
	</body>
</html>
```

## Local vs global
```php
<?php
$a = 1; /* global scope */ 

function test()
{ 
    echo $a; /* reference to local scope variable */ 
} 

test();
?>
```

```php
<?php
$a = 1;
$b = 2;

function Sum()
{
    global $a, $b;

    $b = $a + $b;
} 

Sum();
echo $b;
?>
```

```php
<?php
$a = 1;
$b = 2;

function Sum()
{
    $GLOBALS['b'] = $GLOBALS['a'] + $GLOBALS['b'];
} 

Sum();
echo $b;
?>
```

## Static variables
```php
<?php
function test()
{
    $a = 0;
    echo $a;
    $a++;
}

test();
echo "\n";
test();
echo "\n";
test();
?>
```

```php
<?php
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
?>
```

```php
<?php
function test()
{
    static $count = 0;

    $count++;
    echo $count."\n";
    if ($count < 10) {
        test();
    }
    $count--;
}

test();
?>
```

## Functions (note below depends on PHP version! compare 8.x with 7.x with 5.x, for instance!)
```php
<?php
	function add(int $a, int $b) 
	{
		return $a + $b;
	}
	echo add(5, "5 days");
?>
```

```php
<?php declare(strict_types=1);
	function add(int $a, int $b) 
	{
		return $a + $b;
	}
	echo add(5, "5 days"); // returns an error
?>
```

## Args and return types
```php
<?php
	function increment(int $x, int $inc = 1) 
	{
		return $x + $inc;
	}

	echo increment(100, 5); // returns 105
	echo "\n";
	echo increment(5); // returns 6
?>
```

```php
<?php
	function increment(int $x, int $inc = 1) : int
	{
		return $x + $inc;
	}

	$ret = increment(100, 5); // returns 105
	echo gettype($ret);
	echo "\n";
	echo $ret;
?>
```

## Arrays
```php
<?php
$array = array("foo" => "bar",
				"bar" => "foo");

foreach ($array as $key => $value)
{
	echo "Key=" . $key . ", Value=" . $value;
	echo "\n";
}
?>
```

## Error handling
```php
<?php
	function inverse($x) 
	{
		if (!$x) {
			throw new Exception('Division by zero.');
		}
		return 1/$x;
	}

	try {
		echo inverse(5) . "\n";
		echo inverse(0) . "\n";
	} catch (Exception $e) {
		echo 'Caught exception: ', $e->getMessage(), "\n";
	}

	// Continue execution
	echo "Hello World\n";
?>
```
