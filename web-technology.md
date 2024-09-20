---
description: >-
  1.3.3 - Web Technology. A set of programming languages used to build dynamic
  websites
---

# Web Technology

## Languages

There are three languages that you need to be familiar with

* HTML
* CSS
* JavaScript

These three languages work together to define websites, you need to understand the roles of each language and how they interoperate.

| Language | Acronym                   | Role                                                             |
| -------- | ------------------------- | ---------------------------------------------------------------- |
| HTML     | HyperText Markup Language | Defines the structure and content of a webpage                   |
| CSS      | Cascading Style Sheets    | Defines appearance, aesthetics (colour, font, position, spacing) |
| JS       | JavaScript                | Defines behaviour, interactions                                  |

## HTML

Web pages start with a HTML file, this file will either include embedded snippets of CSS or JavaScript, or it will name other resources which are fetched in separate HTTP requests to the web server.

### HTML Tags

Here is the full list of tags that appear in the spec

* \<html> - Wraps the entire document
* \<link> - to link to a CSS file
* \<title> - which sets the title in the browser when on the page
* \<body> - this wraps the content that is rendered in the main page
* \<h1> \<h2> \<h3> - for creating headers
* \<img> - including the src, alt, height and width attributes.
* \<a> - including the href attribute.
* \<div> - For wrapping up chunks of HTML, usually for styling/layout purposes
* \<form> - Creating Web Forms to capture user input
* \<input> - where the input is a textbox (i.e. has the attribute type=”text” and another attribute name to identify it) or a submit button (i.e. has the attribute type=”submit”)
* \<p> - Wrap a paragraph, usually with some space above & below
* \<li> - A single list item within one of the following types of list
* \<ol> - An ordered list, uses numbers in the bullet point
* \<ul> - An unordered list, uses blobs for the bullet points
* \<script> - Include a JavaScript file

### Inclusion Vs Embedding of CSS & JS

In general, if JavaScript and CSS are defined in separate files, it is much easier to share those resources across multiple HTML files. Many web pages are built from several distinct HTML pages. If the JS or CSS is embedded within the HTML page it will need to be repeated on each page.

## CSS

Learners are expected to be able to use CSS in the following ways

* directly inside elements using the style attribute \<h1 style=”color:blue;”>
* Inside \<style> tags within the HTML \<head> section
* external style sheets.

Here is a Repl that demonstrates all three methods of importing CSS.

{% embed url="https://repl.it/@MarlingSharp/css-demo#index.html" %}
Demonstrate methods of applying CSS
{% endembed %}

### CSS Selectors

In the style sheets they should be able to use CSS to define the styling of elements. Elements can be selected using

* Tag names
* Classes
* Identifiers

This Repl demonstrates all three methods, the style rules are all in an external sheet.

{% embed url="https://repl.it/@MarlingSharp/css-selector-demo#index.html" %}
CSS Selector Demo
{% endembed %}

### CSS Properties

Learners are expected to be familiar with the following properties

```
body {
    background-color: red;
    border-color: black;
    border-width: 1px;
    color: #00ffff;
    font-family: Arial, Helvetica, sans-serif;
    font-size: x-large;
    height: 200px;
    width: 100px;
}
```

## JavaScript

This language is used to add interactions and behaviour to web pages. This has become so sophisticated that web applications are often indistinguishable from full desktop applications.

Here is a Repl that demonstrates different ways to react to a button being clicked.

* The alert() function called directly on the onclick handler.
* The click handler is a function that is defined in a script tag within the page head.
* The click handler is a function that is defined in a separate script file
* The click handler is registered after the window has loaded (in the separate file)

{% embed url="https://repl.it/@MarlingSharp/javascript-inclusion-demo#index.html" %}
JavaScript Button Handlers
{% endembed %}

### Form Handling

Here is a demo Repl that has a form which asks the user a maths question and validates the players answer within the web page.

{% embed url="https://repl.it/@MarlingSharp/year13-web-tech" %}
Dynamic Web Page
{% endembed %}

One of the main uses of JavaScript is to validate forms before the data is submitted to the server.

## Multiple Page Demo

Websites are normally built from multiple pages, to link between pages use the following tag

```
<a href='./otherPage.html'>Click Here</a>
```

Here is a repl that demo's how to do this

{% embed url="https://repl.it/@MarlingSharp/multi-page-demo#index.html" %}

## Client Side vs Server Side Processing

Web pages are commonly used to capture information from users. This information need to be validated by the system, to prevent bad data either corrupting the system, or derailing whatever process the web form is designed to facilitate.

JavaScript allows developers to put validation directly into the web page, preventing bad information from even being submitted in the first place. The advantage of client side validation is that the web page can provide directly timely feedback to the user, without requiring a further round trip to the server.

Client side validation alone is not enough to preserve the integrity of a system, since it is usually possible to submit information directly to web services, without using the web interface at all. The server needs to protect itself centrally.
