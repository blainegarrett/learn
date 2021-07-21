# Session 2: Basic Content Formatting

## Overview
In this session we'll introduce some HTML tags for basic content formatting. If you use Google Docs or the text editor in something like Wordpress, these tags should be fairly familiar. Understanding these tags will give you the basics for understanding how these tools manipulate HTML and will allow you to manually make changes to content when needed.

## Commonly Used Formatting

### Emphasis 
To give a piece of text emphasis, you can use the `em` HTML tag. Semantically, this means the contents are distinguished in the context of the surrounding text. In practice, browsers will render this text with an italic font and a screen reader will pronounce the words with an emphasis, using verbal stress.

Example:

```
This is <em>emphasized</em> text.
```
This will render as:

> This is <em>emphasized</em> text.

### Strong 
To give a piece of text a "strong" emphasis, you can use the `strong` HTML tag. Semantically, this means the text is more important in the context of the surrounding text. In practice, browsers will render this content in a bolder font and screen readers will pronounce the words with an extra gusto.

Example:

```
This is <strong>very important</strong> text.
```
This will render as:

> This is <strong>very important</strong> text.


### Semantic Note
Note: Alternative tags for `strong` and `em` are the `b` tag and `i` tag respectively. They can be used interchangeably for visual purposes and are quite common "in the wild". However, the semantic meaning is ignored when using the `b` or `i` tags and, for example, screen readers won't pronounce the text with the same emphasis as it would for the `strong` and `em` tag. It is just something to keep in mind.

Example:
```
This is <i>italic</i> text.
This is <b>bold</b> text.
```

### Underline
Another common HTML tag is the `u` tag. In practice, it will give the contents an underline. 

Example:

```
This is <u>underlined</u> text.
```
This will render as:

> This is <u>underlined</u> text.

Note: Use this tag rarely as it can be confused with the default visual rendering of links. Additionally, it has no real semantic meaning and is mostly used for display purposes.

### Links
Links (officially known as *hyperlinks*) are a foundational concept on the web. When interacted with (clicked, etc) they can take you to a new piece of content or website. The tag we use to make a hyperlink is the `a` tag. 

In the most common usage, they require a `href` *attribute*. The `href` attribute (standing for *hypertext reference*) is the `url` to where you want the user to navigate to when clicking the link. 

Example:
```
Visit <a href="https://www.mplsart.com">MPLSART</a> to find local art events.
```

This renders as:
> Visit <a href="https://www.mplsart.com">MPLSART</a> to find local art events.

Notes:
 - By default, browsers will render the content of the `a` tag with an underline and typically with a blue font color.
 - The value of the `href` attribute should start with *https://* or similar. It is a common mistake to use, for example, *www.example.com/...* or simply *example.com/...*, however these links will not take you to the expected location. We'll cover the ins and outs of url in another section.
 * More advanced usage of hyperlinks and the `a` tag are covered in a future section.


### Line Breaks
The `br` tag is used to visually force a line break within content. It has no real semantic meaning. In most HTML editors (Wordpress, etc), pressing the *SHIFT - ENTER* key will create a new `br`. Note, the `br` tag cannot contain any *children*.

Example:
```
Line 1<br />
Line 2
```
> Line 1<br />
Line 2


<br />
<br />

## Less Commonly Used Formatting

There are many other less commonly used HTML tags for basic contant formatting. As you might run into several of these in "the wild", we'll list them out here. 

## Delete and Insert 
Semantically, the `del` tag is used to designate content that is intended to be removed but remains in the document. In practice, browsers will render this text with a horizontal line through it.

Example: 
```
<del>This text should be removed.</del>
```
> <del>This text should be removed.</del>

Similarly, the `ins` tag is intended to designate text that should be inserted.

```
<ins>This text should be removed.</ins>
```
> <ins>This text should be removed.</ins>

Note: As with the `b` and `i` tags, alternatives to the `del` are `s` and `strike`. While `del` has a semantic meaning, it is typically used to simply render text with a visual strikethrough. 

## Superscript and Subscript 
The `sup` and `sub` tags are used to visually render text as *superscript* and *subscript* respectively. In practice these are used to display mathematical formulas (eg. exponents) or to visually create footnotes. They are sometimes incorrectly used to make smaller text.

Example:
```
2<sup>2</sup> + 3<sup>3</sup> = 31
The first version of HTML was written by Tim Berners-Lee in 1993<sub> <a href= "https://en.wikipedia.org/wiki/Tim_Berners-Lee">1</a></sub> 
```
>2<sup>2</sup> + 3<sup>3</sup> = 31
>
>The first version of HTML was written by Tim Berners-Lee in 1993<sub><a href="https://en.wikipedia.org/wiki/Tim_Berners-Lee">1</a></sub> 

## Quotations
To capture the semantic meaning When displaying a quote, use the `blockquote` tag for long quotes and `q` for shorter quotes. Browsers will typically display the former with an indent and display the later wrapped in quote marks.

Example:
```
<blockquote>Pretend this is a long quote from your favorite author.</blockquote>

Some argue HTML is <q>a programming language</q>, but life is too short to argue about such things.
```

Example of `blockquote`:
> <blockquote>Pretend this is a long quote from your favorite author.</blockquote>
>

Example of `q`:
> Some argue HTML is <q>a programming language</q>, but life is too short to argue about such things.

<br />
<br />

## More Complex Tags
The above tags are primarily focused on text formatting. The following introduce some other common tags.

## Paragraphs and Containers
There are three primary container tags - each with different meanings.

### Spans
The `span` tag is a simple wrapper tag. It doesn't impose any semantic meaning nor have any visual styling on its own. It is used to contain logically similar text and tags and usually used to apply css styling. It may contain any of the above text formatting tags including links, etc. 

Example:
```
<span>This is a bit of text</span><span>This is a bit of text</span>
```
> <span>This is a bit of text</span><span>This is a bit of text</span>

### Div
The `div` tag is much like the span tag in that it is a wrapper with no real semantic meaning. However, unlike the `span` tag, it does create a visual line break after the contents.

Example:
```
<div>This is a block of text</div><div>This is a block of text</div>
```
> <div>This is a block of text</div><div>This is a block of text</div>


### Paragraphs
The `p` tag is used to designate its contents as a logical paragraph of text. It may contain any of the above text formatting tags including links, etc. It may contain `span` tags but not `div` tags. By default, the paragraph tag creates a visual line break after its contents. In most HTML editors (Wordpress, etc), pressing the *ENTER* key will create a new `p`.

Example:
```
<p>This is block of text</p>
<p>This is <i>another<i> block of text</p>
```
> <p>This is block of text</p>
> <p>This is <i>another<i> block of text</p>

## Lists

### Unordered Lists
The `ul` tag defines an unordered (bulleted) list. The children of a `ul` should be one ore more `li` (list item) tags.

```
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
```
><ul>
>  <li>Item 1</li>
>  <li>Item 2</li>
></ul>




### Ordered Lists
Ordered lists behave the same as unordered lists, but assume that the child `li` elements have an important order that is visually displayed.
```
<ol>
  <li>Item 1</li>
  <li>Item 2</li>
</ol>
```
><ol>
>  <li>Item 1</li>
>  <li>Item 2</li>
></ol>

The starting number and the bullet can be visually controlled via the *start* and *type* attribute respectively. 


```
<ol type="I" start="10">
  <li>Item 1</li>
  <li>Item 2</li>
</ol>
```
><ol type="I" start="10">
>  <li>Item 1</li>
>  <li>Item 2</li>
></ol>

Note: The *type* attribute can be any of:
 - 1 decimal numbers
 - A - uppercase letters
 - a - lowercase letters
 - I - uppercase roman numerals
 - i - lowercase roman numerals


### Nested Lists
TODO: Write bits
```
<ol>
  <li>Item 1</li>
  <li>Item 2
  
  <ul>
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
</li>
</ol>
```
><ol>
>  <li>Item 1</li>
>  <li>Item 2  
>  <ul>
>    <li>Item 1</li>
>    <li>Item 2</li>
></ul>
></li>
></ol>
