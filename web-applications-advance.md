---
title: "PHP, JavaScript, MySQL"
author: [Maria Xenophontos]
date: "2019-08-13"
lang: "en"
...

# Web Applications basics

## Web Content delivery:
1. *Web browser* sends a request for the `index.html`
2. *Web server* looks in its directory contents for the file and sends the file's
contents to the **browser**
3. *Web browser* receives the `index.html` renders the content and if there are 
HTML tags with `src` attributes, it send a request for the file the attribute
points to, to the server.
4. Web server interprets the request and sends the file to the browser
5. Web browser displays the e.g. image that the file held.

## Document Root:

The document root of a web server is the trailing slash in the full URL e.g. if
domain is *mydomain.com* with URL *https://mydomain.com/* then the document root
is the directory represented by the trailing slash (/). The document root is the
place where the web server begins looking for files requested by the web
browser.

The `index.html` file is the default file users see when they navigate to a
specific directory in a website. If the server allows directory browsing and
index.html is not available the user sees the list of files in that directory.

# HTML structure and Cascading Style Sheets (CSS)

`.jsp` Java Server Pages, `.aspx` Microsoft Active Server Pages and `.php`
Hypertext Preprocessor files all contain HTML in addition to the programming
language. The code in such files is however executed on the server and the
output on the Client side is HTML.

# Required HTML tag pairs

* `<!DOCTYPE html>`; the document type decaration
* `<html></html>`
* `<head></head>`; information put here is descriptive of the web page but it is
  nit displayed by the browser.
* `<title></title>`; places the text it encloses at the top of the browser
  window. Text placed between these tags also identifies the page on the
  browser's bookmarks.
* `<body></body>`; places the text it encloses in the main display area of
  the browser window.

# Common HTML tag pairs

* `<p></p>`; paragraph tag
* `<a></a>`; constructs anchors and hyperlinks on the Web. e.g.

    ```
    <a name="top"></a> ... <a href="top">Take me to the top</a>
    ``` 
    or if linking from a different page
   
    ```
    <a href="https://www.mydomain.com/about.html#top">About page</a>
    ```
    Relative paths are also allowed.
    
    ```
    <a href="mailto:user@domain.com">Email me</a>
    ```
* `<hr>`; horizontal rule line
* `<br>`; forces line break
* `<h1>Biggest heading</h1>`...`<h6>Smallest heading</h6>`; logic dictates only
  one `<h1>` heading. 

An *empty tag* issues an HTML command without enclosing any text in the page,
e.g. `<br>` and `<img>`for line breaks and images respectively as opposed to
`<body></body>`

# HTML semantic elements
* `<header></header>`; use to include introductory info about the element it is
  contained within
* `<footer></footer>`; similar to header but usually holds info such as
  copyright and related sources
* `<nav></nav>`; use for navigational elements e.g.
    
    ```
    <ul><li><a href="#">About us</a></li></ul>
    ```
* `<section></section>`; use for thematic grouping of content
* `<article></article>`; use for anything that is **complete** or
  **self-contained** composition in a document
* `<aside></aside>`; use for peripheral content, e.g. additional explanation,
  resources etc

# CSS

A style sheet sets formatting characteristics, e.g. typeface control, line
spacing, margins and page borders etc.

> An *internal style sheet* is placed directly within a web page whereas an
*external style sheet* exists in a seperate document and is linked to a web page
by a special tag.

```css
body{
    /* semicolons are used to seperate style rules */
    font-size: 10pt;
    /* Order in which browser searches for fonts to use.
    * If the ones listed are not available use any sans-serif font.
    */
    font-family: Verdana, Geneva, Arial, sans-serif;
    color: black;
    line-height: 10pt;
    padding-left: 5pt
}
h1{
    font: 14pt Verdana Geneva, Ariel, sans-serif;
    font-weight:bold;
}
...
```
To link a style sheet in an HTML document include a `<link>` tag in the `<head>`
section of the document e.g.

```html
<!-- Style sheet is assumed to be stored in the same folder as the HTML doc -->
<link rel="stylesheet" type="text/css" href="styles.css">
```

Style properties in CSS are grouped into:

1. Layout properties: affect the positioning of elements
    * e.g. Display property defines how an element is displayed with respect to
      other elements (block,list-item, inline, none)
2. Formatting properties: affect the visual display of elements
    * e.g. Border property that adds a visible boundary on the element.
    * Font family property

A *Style class* is a custom set of formatting specifications that can be
applied to any element in a web page. *Style Classes* can be defined for a 
single *CSS selector* with:

```css
/* h1 is the selector used to identify tags on a page
 *font is the size property and
 *36pt 'Comic Sans' is the value of it
 */
h1.silly{font: 36pt 'Comic Sans';}
```

or for all HTML elements with:

```css
.silly{font: 36pt 'Comic Sans';}
```
To apply a specific Style Class to an element one has to specify the class in
the tag, e.g. `<h1 class="silly">foo</h1>`

*A Style ID* is a custom set of formatting specifications like a style class
with the difference that it can only be applied to *one element per web page.*

Style ID example:

```css
p#title{font: Verdana}
<p id="title">Some title</p>
```
Style instructions can be included in the `<head>` tag of HTMLs wrapped in
`<style></style>` tags or under the attribute *style* of all elements e.g.
`<span style="color:green">Color me green.</span>`.

# CSS Box Model

* It describes the way in which every block-element has the potential for a
 margin, border, padding wrapped around it (;listed from the outside inward).
* The total width of an element is the sum of: *width + margin-left,
  margin-right + border-left + border-right + padding-left + padding-right*

# Positioning

The positioning of an element can be *absolute* (i.e. fixed) or *relative* to
the preceding or parent element. The type of positioning is defined by the
*position* property which can have any of the values *static, relative, absolute
and fixed* and tweaked by the properties *left, right, top, bottom*. Elements
can be arranged to overlap using absolute positioning and their order can be
defined by the *z-index* which takes values from 0 to n. An element with
*z-index* of 0 will be placed on the bottom of the stack whereas one with
*z-index* of n will be placed on the top.

## Text Flow

How text and other elements mix is controlled by the properties:
* *float*: determines how the text flows round an element and takes values
  *left, right*. e.g. `<img float="left" src="foo.jpeg">` places the image to
  the left of flowing text
* *clear*: stops the flow of text around an element
* *overflow*: contains the flow of the text when an element is too small to fit

# JavaScript

* It is an interpreted language *i.e.* the browser executes each line of code as
  it comes to it
* It can be added in:
    * the body of a page
    * between the `<head>` tags if adding functions
    * within HTML tags like `<body>` and `<form>` as an *event handler*
    * in a separate `.js` script and added to `<head>`using the
      `<script></script>`. One or more `<script>` tags can be added to the
      `<head>`

```html
<script type="text/javascript" src="filenae.js"></script>
```

* It allows remote scripting/asynchronous JavaScript and XML (AJAX) for
  communicating with a server. Via AJAX data can be retrieved from a server
  without loading a page or requiring to be saved.

## Concepts

### Variables *vs* Objects
* **Variables** can only store one piece of data
* **Objects** can simultaneously store several pieces of data and include
  *methods* that work on the objects data.

### Object types

* Built-in objects
* Document Object Model (DOM) are objects representing components of the browser
  and current HTML.
* Custom objects

Almost everything is *case sensitive*

* keywords such as `for` and `if` are lowercase
* Built in objects are first-letter capitalized
* DOM are usually lowercase but the second-half of their methods names' are capitalized

```
// this is a comment in Javascript
/* This
too*/
```

Javascript Object Notation (JSON) is a common way to structure and store
information. Syntax and concept is similar to a python dictionary.

```
var fooJSON = {
    "param1": "value1";
    "param2": "value2"
    }

alert(fooJson.param1); //alerts 'value1'
```
# PHP

* It is a server-side scripting language (*vs* the front-end languages HTML and
  JavaScript)
* How it works with web servers:
    * client submits a request for a web page -> server reads the HTML file ->
      server executes anything wrapped in PHP tags found in the HTML and puts
      the result in the block the code was contained -> HTML sent it back to the
      browser
* `<?php`, `?>` are the standard tags used to include PHP code. `<?` and `?>`
  short tags should be avoided as they are also used for XML processing
  instructions  
* One can slip in and out of PHP and HTML! *i.e.*

```
<?php
<body>
$some_condition =true;
    if ($some_condition) {
        ?>
        <img source="file.jpg">
        <?php
        }
        ?>
</body>
```
# JavaScript vol.2

* concatenation operator is `+`
* `var myarray = new Array(4);`

## Document Object Model (DOM)

* not part of JavaScript *per se* but an API built into the browser
* objects organised into tree-like structure e.g. `window.document.logo_image`.
  Each node in this tree has properties and methods and can be accessed in
  JavaScript.

### Browser object hierarchy

```
window
|
|______ document
|       |    document.title // as set in <title>
|       |    document.URL
|       |    document.referrer // URL of page viewed before current one
|       |    document.images // returns a list of images used in the doc
|       |    document.cookie // read or set a cookie within the doc
|       |    document.write, document.writeln // print text as part of the HTML
|       |
|        _____ links
|       |           document.links.length // returns the number of links on page
|        _____ anchors
|       |           document.anchors.length
|______ location // holds info on currently loaded URL with window.location.href
|            location.protocol, *.hostname, *.port
|            location.pathname // filename path of URL e.g. search in
|                              // somehost/search?q=javascript
|            location.search // query portion e.g. q=javascript
|            location.assign() // load a new doc, takes a URL as argument
|            location.reload() // reload the current doc
|______ history // holds URL data & includes methods to go to previous or next locations
|            history.go() // e.g. history.go(-2) is equivalent to clicking the
back button twice
|            history.back() // same as history.go(-1)
|            history.forward() // same as history.go(1) if available
|______ navigator
|

|
```
### Basic Node Properties

* `nodeName`
* `nodeType` is an integer describing the nodes type:
    * HTML tags = 1
    * text nodes =3
    * document node = 9
* `nodeValue` returns NULL for all nodes except the text node, for which it holds
  the actual text
* `innerHTML` and `innerText` hold the HTML and text content of any node
  respectively

### Basic Node Methods

* `parentNode` is the primary node of an element
* `firstChild`, `lastChild`, `childNodes`, `previousSibling`, `nextSibling`
* `appendChild(new)`, `insertBefore(new, existing)`, `cloneNode(x)`
* `replaceChild(new, existing)`, `removeChild(node)`
* `hasChildNodes()`, returns boolean value

### Document Methods

* `getElementById(id)`, 
* `getElementByTagName(tag)`, returns an array of all elements with a specified
  tag
* `createTextNode(text)`, creates new node with the specified text. It needs to
  be added to the document after creation.
* `createElementTag(tag)`

*Nota bene*: `?` and `:` characters create *conditional expressions*, i.e. they
are a shorthand way of handling `if` conditions. e.g. `value = (a == 3) ? 1 : 0`
sets `value` to `1` if condition is met.

## Defining an Object

```
// this is a constructor function for defining an object that holds 
// business card information
function Class(name, email, address, phone){
    // `this` is used to refer to the current object -- the one being 
    // created by the function
    this.name = name;
    this.email = email;
    this.address = address;
    this.phone = phone;
    this.printCard = printCard; // add printCard function as a method to this
    object
    }
```

## Defining an Object Method

```
function printCard(){
    var name_line =  "Name: " + this.name + "<br/>\n";
    var email_line =  "Email: " + this.email + "<br/>\n";
    var address_line =  "Address: " + this.address + "<br/>\n";
    var phone_line =  "Phone: " + this.phone + "<br/>\n";
    document.write(name_line, email_line, address_line, phone_line);
    }
```

* New objects are created with `var x = new Card("John Do", "jdo@jdo.com", "Some
address", "22xxxxxx");`
* Though not advised methods and properties can be added to JavaScript built-in
objects with `prototype`  e.g. `String.prototype.heading = someFunction;`

*Nota Bene*: the conditional operator `===` checks if the values are equal in
both value and type.

## Event handling

* actions/functions invoked for `onclick`, `onmousedown`, `onmouseup` etc
* In Chrome, Safari, Firefox, events are automatically passed to the event
  handler function but in Internet Explorer it is stored in `window.event`
* Event properties differ between web browsers, always add a line checking if
  event is present `if (!e) e = window.event;`

## JQuery

* it is a JavanScript library
* it can be loaded from a local machine or from a content delivery network such
  as the one hosted by Google (the url for the `jquery.min.js` file can be
  passed to the `src` parameter of the `<script>` tag). The latter is faster as
  the user may have that file cached.
* `$("#someElement")` to get an element that has an ID someElement
* `$(".someClass")` to get the elements of class someClass
* the `$().ready` handler ensures that nothing within the page has been
  manipulated until a state of DOM readiness has been detected. Thus all primary
  commands should be wrapped by this handler.

  ```
  $().ready(function() {
      // Jquery code goes here
  });
  ```
* JQuery's `show()`, `hide()`, `toggle()` can be applied to a collection of
  elements and are easier to use than manipulating the value of the `display`
  property of an element's style object.
* JQuery has its own syntax for handling events; you can attach event handlers
  to elements or collection of elements e.g. `$("a").click(function(){//execute
  this code when any anchor element is clicked});`

## AJAX: remote scripting

* a browser feature that enables JavaScript to work with files on a web-server. 
* it is basically JavaScript's ability to use the built-in object
  `XMLHttpRequest`
* JavaScript can send data to a server-side program using the `GET` and `POST`
  methods. In a `GET` request the data is encoded in the URL that loads the
  program , whereas in a `POST` request the data is sent separately.
* Functions that handle making a request and receiving the result can be
  provided as an AJAX library (\*.js) that is referenced in the pages as any
  external script.

### How an AJAX request works

1.  script creates an `XMLHttpRequest` object and sends it to the web server.
Since it is an **Asynchronous** JavaScript it can continue performing other
tasks while waiting for a server response.
2.  the server responds by sending the contents of a file/output of a program.
3.  when the response arrives, a Javascript function is triggered to act on the
data
4.  script displays the data from the server usually using the DOM, hence the
page does not need to refresh.

### XML

* a markup language designed to store and transport data
* not so commonly used any more since it is easier to transfer data in JSON
  format

## Using XMLHttpRequest to communicate with a server

```
var ajaxreq = new XMLHttpRequest();
// send data from filename to the server with method GET
// ajaxreq.open("GET", "filename");
/* opens the search.php script stored on the server and sends the value John to
it as the query parameter */
ajaxreq.open("GET", "search.php?query=John");
/* the XMLHttpRequest object has a property readyState with values 0-4
(0 for a new request and 4 for complete) that can be accessed with the
following handler and invoke MyCustomFunc once request is ready */
ajaxreq.onreadystatechange = MyCustomFunc;
// if the POST method is used instead then the argument to send() is the data
ajaxreq.send(null);
```


