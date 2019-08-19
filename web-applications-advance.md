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
