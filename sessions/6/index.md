# Session 6: CSS Basics


## Overview
Now that we have a basic understanding of HTML, we're going to learn some CSS basics to apply to that HTML. When we're done with this section, we'll have a basic understanding of what aspects of HTML we can style and how we go about it. 

<br />

### Why Does CSS Exist?
In the previous sections, we learned the basics of HTML. While some HTML tags render in the browser with certain style applied (eg. the `b` tag looks bold), HTML is more about semantic meaning and structure than visual display. However, we can use CSS ("Cascading Style Sheets") to control most aspects of visual display of HTML content.

Think of HTML like the materials used to build houses. Each has their own properties that make them useful: concrete is strong and good for foundations whereas shingles help keep water from entering the house. However, these materials are pretty drab by themselves. Assuming we're not building the [Brutalist](https://en.wikipedia.org/wiki/Malcolm_Moos_Health_Sciences_Tower) equivalent of a website, we can make it look nice with CSS. However, CSS isn't used merely to apply colors, it can be used to control placement, animations, and a host of other things. 

<br />

### CSS Declarations
At its core, CSS is a set of *declarations*. Very similar to HTML attributes, declarations come in name/value pairs. 

For example, if we want to make some text bold, we can use the `font-weight` declaration with a value. 

```
font-weight: bold
```

Also like HTML attributes, we can have multiple declarations. In CSS, each one is separated by a semicolon.

```
font-weight: bold; color: blue
```

When the above declarations are applied to an HTML element, the text inside it will be bold and blue. 

<br />

### Inline CSS 
The easiest way to apply CSS declarations to an HTML element is to apply them "inline". To do this, we can use a special HTML attribute on our element named `style`. The value is the string of semicolon separated CSS declarations. 

Example:
```
<a href="#" style="font-weight: bold; color: blue">Blue &amp; Bold</a>
```
Renders as:
> <a href="#" style="font-weight: bold; color: blue">Blue &amp; Bold</a>

<br />

This is fine for most things, but it can get out of control quickly. Just imagine if you updated every `a` on your site to be bold and blue and then later realized you wanted to change the shade of blue. That's a lot of HTML to update! We'll learn a better way next.


<br />

### CSS Rules 
CSS rules are simple way to target a group of things to apply CSS declarations to. The syntax is fairly straightforward:
```
<selector> { ...list of declarations ... }
```

So for example, we can now easily define a CSS rule to make all the links bold and blue. 

```
a { font-weight: bold; color: blue }
```
Here, we have a very simple "selector", `a`, that merely selects all HTML links (`a` tags). 

However, we can do a lot more than simply select HTML tags by their tag name. 

🧠 When CSS is applied "inline", no "selector" is needed so it implicitly applies to the HTML element that the style attribute is on. It's implicit.

<br />

## Common CSS Selectors

### HTML Tag Selectors
As illustrated above, we can target all HTML tags with a common tag name. The selector is simply the tag name.

```
a { font-weight: bold; color: blue }
img { width: 100%; }
```

<br />

### ID Selector
In a previous section covering internal links, we introduced the "id" HTML attribute. When combined with a url *fragment* (the optional # part of a url), it can be used to force the browser to scroll to a specific piece of content on a page. Every ID is supposed to be unique to a single HTML element. We can leverage this to "select" a single HTML element to apply CSS to. The syntax is:

```
#<id-attribute-value> { ... } // Note the # prefix
```
So for example, we can make the "Overview" heading at the top of the page underlined using:

```
#overview {
 text-decoration: underline
}
```
Scroll to the top of the page and check it out!

<Style>
   #overview {
      text-decoration: underline
   }
</Style>


### Classname Selector
While ID selectors can only target a single HTML element and HTML tag name selectors target all of a certain type, using class names allows for a lot more flexibility. You can apply a class name to any HTML element using an HTML attribute with the name `class` and with a value of the classnames (separated by spaces).

If we have the following HTML: 
```
<a href="...">link 1</a>
<a href="..." class="bold-links">link 2</a>
<a href="..." class="green-links">link 3</a>
<a href="..." class="bold-links green-links">link 4</a>
```

we can use the following rules:
```
.bold-links {
   font-weight: bold
}
.green-links {
   color: green
}
```

This will produce the following:
> <a href="...">link 1</a>
> <a href="..." class="bold-links">link 2</a>
> <a href="..." class="green-links">link 3</a>
> <a href="..." class="bold-links green-links">link 4</a>
> <Style>
>    .bold-links {
>    font-weight: bold
> }
> .green-links {
>    color: green
> }
> </Style>

Notes: 
- "link 1" has no class name and is thus has no style declarations applied
 - "link 2" has just the `bold-link` class name and we have a rule that selects elements with that class name and makes them bold. 
 - "link 3" has just the `green-link` class name and we have a rule that selects elements with that class name and makes them green.
 - "link 4" has both the `bold-link` and `green-link` class names and surprise surprise two different rules apply. 

<br />

🧠 Multiple rules applying to the same HTML element is the *Cascading* part of Cascading Styles Sheets. 

<br />

### Chaining Selectors
In the first session, when we introduced HTML, we noted that there is a parent/child relationship between HTML elements. Specifically, every element has at most one parent HTML. This is conceptually similar to the path of file folders. Thinking back to the URL section, the *path* to a file is the list of parent folders. We can apply a conceptually similar approach by chaining CSS selectors to even further target which HTML elements we want to apply styles too.

Given the following HTML
```
<a href="#">regular link</a>
<ul>
<li><a href="#">link 1</a></li>
<li><a href="#">link 2</a></li>
</ul>
<ul class="green-list">
<li><a href="#">link 3</a></li>
<li><a href="#">link 4</a></li>
<li><a href="#" class="bold">link 5</a></li>
</ul>
```
... and the following CSS:
```
li a { color: red }
ul.green-list a { color: green}
li a.bold { font-weight: bold}
```

we get: 
> <a href="#">regular link</a>
> <ul>
>  <li><a href="#">link 1</a></li>
>  <li><a href="#">link 2</a></li>
> </ul>
> <ul class="green-list">
>  <li><a href="#">link 3</a></li>
>  <li><a href="#">link 4</a></li>
>  <li><a href="#" class="bold">link 5</a></li>
> </ul>

<style>
li a { color: red }
ul.green-list a { color: green}
li a.bold { font-weight: bold}
</style>

<br />

🧠 Selectors are extremely powerful and can also do things like [select every other element](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-child), or [select elements with attributes that start with certain words](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors). We will not be covering some of these advanced usages until later, but you can check out the links to get a preview and try them out if you like.

<br />
<br />


## How To Apply CSS When Using Rules
Using CSS declarations "inline" above is only one way to apply CSS to HTML. However, when using CSS rules, you need to collect them somewhere in your HTML content. There are two options:

### Using the Style HTML tag
You can put all or some of your CSS rules into a special HTML `style` tag in your HTML content. 

```
<style>
.bold-links {
   font-weight: bold
}
.green-links {
   color: green
}
</style>
```

Typically, there will be one `style` attribute and it will be a child of the `head` tag. However, you can have multiple style tags and they can go anywhere in your content. 

### External CSS File
You can put all or some of your CSS rules into a separate file. You can include this in your HTML code in the `<head>` tag:

```
<head>
  ...
  <link rel="stylesheet" href="url-to-file.css">
   ...
</head>
```
Like an `img` tag with a `src` attribute, the browser will see this `link` tag with the `rel` attribute of "stylesheet" and load the file at the `href` url and apply the CSS rules to the content. 

<br />

### Combining Methods and Specificity
It is worth noting that you can use multiple external stylesheet files, multiple `style` tags, and inline styles all together. When rules conflict, the browser will take several things into consideration. Inline styles will almost always take precedence, followed by the `style` tags in reverse order that they appear. Finally, external stylesheets will apply (also in reverse order that they appear).

Additionally, when using selector chaining, the browser will look at how specific the selectors are to determine which conflicting declaration to apply. The most specific will supersede any other.

<br />

### Takeaways
CSS is used to control the visual display of HTML. Using a CSS rules and selectors, we can apply CSS declarations to any HTML element we want. 


## Wrapping Up
We now understand some basics of CSS and how to apply CSS to our pages. If you get bored, you can check out the [CSS Zen Garden](http://www.csszengarden.com/). 


## Homework
In the playground, make a HTML list of names of real cities and a HTML list of fictitious cities. Make the real cities have blue text and the fictitious have green text. Using class names, make each of the cities you have been bold and each of the places you want to go underlined - both using CSS declarations. Bonus: figure out how to make the blue and green colors not god awful looking using the hex color syntax (will require research not covered above). 