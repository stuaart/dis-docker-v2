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


## Variable scoping, handling exceptions
```html
<html>
  <body>
  <h1>My First Web Page</h1>
	<script type="text/javascript">
    if (true)
    {
      var a = 10; // 'function' scope meaning it's only declared once
      {
    	  var a = 20; /* 'function' scope means it doesn't matter if it's in a block,
                       it will still exist outside of the block */
        document.write("<p>a=", a, "</p>"); // a has been updated
      }
      let b = 10; /* 'block' scope meaning that it does not exist outside a block the 
                     variable is defined in */
      {
    	  let b = 20; /* assignment only happens locally and 'b' outside this block is 
                       unaffected */
        document.write("<p>b=", b, "</p>");
      }
      // we can access both variables but *which* is accessed differs
      document.write("<p>a=", a, "</p>"); 
      document.write("<p>b=", b, "</p>");
    }

    // outside of the if-block we encounter trouble for the let-defined variable
    document.write("<p>a=", a, "</p>");
    try // try-catch is very similar to PHP, Python etc.
    {
      document.write("<p>b=", b, "</p>");
    } catch (err) { 
      document.write("<p>b=not defined!</p>");
    }
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