JavaScript examples
===================
Try the following examples using an online JavaScript sandbox e.g., https://jsfiddle.net


## Basic JS inline
```html
<!-- inserting an element -->
<html>
  <body>
    <h1>My First Web Page</h1>
    <script type="text/javascript">
      document.write("<p id=\"demo\">" + Date() + "</p>");
    </script>
  </body>
</html>
```

```html
<!-- overwriting an element -->
<html>
  <body>
    <h1>My First Web Page</h1>
    <p id="demo"></p>
	<script type="text/javascript">
		document.getElementById("demo").innerHTML = Date();
	</script>
  </body>
</html>
```

## Writing to the HTML stream
```html
<html>
  <body>
  <script type="text/javascript">
    /* The code below will write 
       one heading and two paragraphs */
    document.write("<h1>This is a heading</h1>");
    document.write("<p>This is a paragraph.</p>");
    document.write("<p>This is another paragraph.</p>");
    // Script ended
  </script>
  </body>
</html>
```

## Form elements
```html
<html>
  <body>
    <h1>Demo of accessing form elements</h1>
    <form id="myForm" action="newpage.php">
      First name: <input type="text" name="fname" value="Stuart"><br/>
      Last name: <input type="text" name="lname" value="Reeves"><br/>
      <input type="submit" value="Submit">
    </form>

    <p>Click the "Try it" button to get the URL for where to send form data when the form is submitted.</p>
    <button onclick="myFunction()">Try it</button>

    <p id="demo"></p>

    <script>
      function myFunction() {
        var n = document.getElementById("myForm").action;
        document.getElementById("demo").innerHTML = n;
      }
    </script>
  </body>
</html>
```

```html
<!-- form validation script borrowed from w3c: https://www.w3schools.com/js/js_validation.asp -->
<html>
<head>
<script>
function validateForm() {
  let x = document.forms["myForm"]["fname"].value;
  if (x == "") {
    alert("Name must be filled out");
    return false;
  }
}
</script>
</head>
<body>

<h2>JavaScript Validation</h2>

<form name="myForm" action="/action_page.php" onsubmit="return validateForm()" method="post">
  Name: <input type="text" name="fname">
  <input type="submit" value="Submit">
</form>

</body>
</html>
```


## Scoping
```html
<html>
  <body>
<script type="text/javascript">
{
	document.write("<h1>This is a heading</h1>");
	document.write("<p>This is a paragraph.</p>");
	document.write("<p>This is another paragraph.</p>");
}
</script>
  </body>
</html>
```

```html
<html>
  <body>
  <h1>My First Web Page</h1>
	<script type="text/javascript">
	  var a = 10;
    {
    	var a = 20;
    }
    let b = 10;
    {
    	let b = 20;
    }
    document.write("<p>a=", a, "</p>");
    document.write("<p>b=", b, "</p>");
	</script>
  </body>
</html>
```

```javascript
// Global variable
let globalVariable = "This is a global variable";

// Declaring another global without using var
global = "another global";

function myFunction() {
  // Local variable
  var localVariable = "This is a    local variable";
  // Printing the global and the local
  console.log(globalVariable); 
  console.log(localVariable); 
  /* Reusing the name above to make new assignation (gets destroyed anyway) */
  global = "this is a fake global";
}

```

## Comments
```html
<html>
  <body>
	<script type="text/javascript">
		/* The code below will write 
		   one heading and two paragraphs */

		document.write("<h1>This is a heading</h1>");
		document.write("<p>This is a paragraph.</p>");
		document.write("<p>This is another paragraph.</p>");
		// Script ended
	</script>
  </body>
</html>
```

## Event handlers
```html
<input type="button" onClick="javascript:doButton()">
<select onChange="javascript:doChange()">
<a onClick="javascript:doSomething()">link text</a>
<form onSubmit="javascript:validate()">
<body onLoad="javascript:init()">

<html>
<head>
	<title>My Page</title>
</head>
<body>
	<p>
	<a href="myfile.html">My page (no mouseover)</a>
	<br/><br/>
	<a href="myfile.html" onMouseover="window.alert('Hello');">My page (with mouseover)</a>
	</p>
</body>
</html>
```

```html
<html>
<head>
	<title>My Page</title>
</head>
<body>
	<p>
  <form>
  <input type="button" value="Press"
         onClick="window.alert('Hello');">
  </form>
  </p>
</body>
</html>
```

## Variables (and scope again)
```html
<html>
  <body>
    <h1>Variable scope</h1>
    <script type="text/javascript">

      n = 1;
      let m = 2;
      var o = 3;
      {
      	let z = 15;
      	var y = 25;
      }
      function myvar()
      {
      	var a = 10;
      	let b = "hello";
        console.log(typeof a); // prints the type of var a to the console - a useful debugging option
      }
    </script>
  </body>
</html>
```