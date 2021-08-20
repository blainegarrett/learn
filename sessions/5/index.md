# Session 5: Special Characters


## Overview
Now that we have a basic understanding of HTML and are familiar some common tags, you might be asking what happens if we need to show HTML syntax in your rendered HTML. No? Perhaps even less so, you might be wondering how to use characters used for HTML syntax. What about emojis? In this session we'll go down a small rabbit hole.

### Why is this a problem?
When you write HTML, the browser tries to interpret what you wrote into valid HTML markup. When it runs across characters that might otherwise be used in HTML markup, the browser can get confused thinking it might be HTML. The browser may render the output unexpectedly.

**Common Problematic Characters**
- `<` -  less than sign
- `>` - greater than sign
- `"` - double quote (used in attributes)
- `&` - We'll learn why ampersand is an issue shortly.

So how do we actually display these characters?
<br />
<br />

### HTML Encoding to the Rescue
The creators of HTML came up with a convention when you want to use these characters in your HTML markup without the browser interpreting them as HTML: encoding. 

The format is mostly straight forward: an ampersand, followed by the *entity name* of the character, followed by a semi colon.

<br />

Assuming the *entity name* for a double quote is `quot`, then to make a quote, we write `&quot;`.

Example:
```
Call me &quot;Ishmael&quot;
```
becomes:
> Call me &quot;Ishmael&quot;
<br />
This works for the other characters too:
```
0 &lt; n &gt; 100
```
becomes:
> 0 &lt; n &gt; 100

<br />
The reason the ampersand doesn't work, is that it is the prefix for the encoding syntax. So when the browser runs into an `&` it tries to look for the above syntax and may do unexpected things if it doesn't find it. To use an ampersand, use the following syntax:

```
I prefer peanut M&amp;Ms to the regular kind
```

> I prefer peanut M&amp;Ms to the regular kind 

<br />
<br />

### ASCII, Unicode, and Emojis
Early computers could only understand a small set of characters, typically only the American Alphabet, numbers, some punctuation and some special visible and invisible control characters for software purposes. As computers evolved, so too did the set of characters that could be supported, but often in a non-standard way. Finally someone declared that there was only a finite set of allowed characters. This set of characters is called ASCII. All was right in the world.

Then came the Internet and HTML. People wanted more characters to use. What if you wanted to display a copyright notice on your webpage, for example? What if your name was spanish and contained an accent character? 

HTML, specifically, had a solution by leveraging the above encoding logic for this too. So for example: 

```
&copy; Copyright 2020 Michael Pe&ntilde;a
```
> &copy; Copyright 1975 Michael Pe&ntilde;a

<br />
Using this method, a "bunch" of different different characters could be represented. Each one merely requires knowing the *entity name*. All was right in the world again.

<br />
However, trying to name each possible character is obnoxious. Conveniently, each ASCII character was given a 1 byte decimal number index known as the *entity number*. Down at the binary level, the uppercase letter *B* isn't swirling around, its decimal entity number (66) in binary is (1000010). 

That said, HTML started allowing you to use the *entity number* in place of the entity name. This also allowed for a lot more characters to be represented using the same convention.

The above examples using entity codes.
```
Call me &#34;Ishmael&#34;
0 &#60; n &#61; 100
I prefer peanut M&#38;Ms to the regular kind
&#169; Copyright 2020 Michael Pe&#241;a
```
> Call me &#34;Ishmael&#34;<br/>
> 0 &#60; n &#61; 100<br/>
> I prefer peanut M&#38;Ms to the regular kind<br/>
> &#169; Copyright 2020 Michael Pe&#241;a<br/>

Note: There is still the `&` prefix, but it is also followed by `#` to tell the browser the value is the *entity number* (in decimal format).

<br />
The above convention started to break down as more and more characters needed to be supported. The largest *entity number* that could be represented was decimal 127 (0111111 in binary). Much like the 8bit Nintendo had worse graphics than the 16bit Super Nintendo (which in turn had worse graphics than the 64bit Nintendo 64), the character representation needed an upgrade too.
<br /><br />
Eventually, characters stopped having silly *entity names* to memorize and only had *entity numbers*. Instead of 127 different supported characters, this new convetion is capable of supporting 1,112,064 characters. The new convention was is called UTF-8. Finally, since the *entity numbers* started getting so large, support was added to use the hexidecimal numbers instead of just decimal. The prefix using the hexidecimal format became `&#x`. 


*Examples (hexidecimal vs. decimal notation)*

```
&#x188; - &#392; - mongolian characters
&#x2660; - &#9824; - picograms
&#x1F600; - emojis
```

> &#x188; - &#392;<br/>
> &#x2660; - &#9824;<br/>
> &#x1F600; - &#128512;<br/>


### 🧠 Primer on binary, decimal, and hexidecimal numbers
As mentioned before, all data eventually turns into binary data. One *bit* of binary data can either be 1 or 0. This makes it suitable for use with fiber optics (the light is on or off) and punch cards (hole is punched out or not). 8bits strung together makes a *byte*. Since each bit can only have 2 different values, we say that it is "binary" or "base 2". When you need to represent a number larger than 1, you simply add another bit just as you would if you are using decimal numbers. (i.e. one more than 9 is 10).

The numbers 0-5: 
```
0
1
10
11
100
101
110
111
```

Decimal numbers are the numbers you are familiar with. We call these "base 10". One "bit" of decimal data can have the values 0-9. If you need a larger number, you add more bits. The number 612 has three bits.

Hexadecimal numbers are base 16. One bit of hexidecimal data can have up to 16 different values - 0-9, but then also the letters A, B, C, D, E, F. 

The numbers 1 - 17 in hexidecimal:
```
0
1
...
9 
A // 10 in decimal
B 
C 
D 
E 
F
10, // 16 in decimal
11 
12
13
14
15
16
17
```

You can technically represent numbers in any base. Different cultures used different bases for counting and even have vestigial words built into their language for the numbers even though they use base 10 numbers (e.g. Spanish). If this is interesting, check out the <a href="https://en.wikipedia.org/wiki/List_of_numeral_systems">wikipedia article about number systems</a>.

### Assignment Idea
Pick an special character. In the playground, display it using the entity name, decimial notation, and hexadecimal notation. What happens if you use the hexidecimal notation but leave off the `#` prefix and separately the `#x` prefix? 



### Takeaways
HTML provides a couple different solutions to displaying special characters. Sometimes these characters work as-is and sometimes the browser chokes on them. To be safe, use the encoding methods above. Do not attempt to remember every *entity number* or *entity name*. Instead be able to recognize the general pattern when you see it and understand the difference between characters in entity name format, decimal notation, and hexidecimal notation. <a href="https://unicode-table.com/en/html-entities/">Here is an categorized list of all characters and their respective html codes</a>. Again, do not expect to memorize these.


## Presevering Whitespace In HTML
One final thing of note is that HTML doesn't inherently display all the whitespace characters you type. Things like literal spaces, newlines, etc are considered part of the markup and less about the formatting. Generally, newlines are controlled by if a tag is a block tag or not. Additionally, multiple spaces are generally collapsed into a single space. 


Examples:
```
This is      line 1


This is line 4
```
becomes:

>This is      line 1
>This is line 4

Note how the the newlines vanish and the spaces are collapsed. Luckily, HTML has ways around this. 

### Non-Breaking Spaces
In order to have multiple spaces, we need a "non breaking space". This is accomplished using the named HTML entity `&nbsp;`

### Break Tags
We've covered `br` tags before. However, they are a self closing tag that forces a visual line break. Simply put a `<br />` in your text and you have a newline.


Examples:
```
This is &nbsp;&nbsp;&nbsp;&nbsp;line 1<br />
<br />
<br />
This is line 4
```
becomes:

>This is &nbsp;&nbsp;&nbsp;&nbsp;line 1<br />
><br />
><br />
>This is line 4

<br />
<br />

### Preformatted Text
HTML has one more magical mechanism to preserve whitespace: the `pre` tag. HTML will still be rendered within the `pre` tag, but any whitespace will be preserved as is.


Example: 
```
<pre>
  <q>bark bark</q> -- Doggo
   __
o-''|\_____/)
 \_/|_)     )
    \  __  /
    (_/ (_/ 
</pre>
```

becomes: 

> <pre>
>  <q>bark bark</q> -- Doggo
>   __
>o-''|\_____/)
> \_/|_)     )
>    \  __  /
>    (_/ (_/ 
></pre>

<br />
whereas, without the `pre` tag, it becomes:

>  <q>bark bark</q> -- Doggo
>   __
>o-''|\_____/)
> \_/|_)     )
>    \  __  /
>    (_/ (_/ 

<br />
<br />

### Takeaways
HTML doesn't display the whitespace you type. Using a combo of `br` tags, `&nbsp;` characters, and `pre` tags, you can accomplish what you want. If you are bored, check out the <a href="https://www.asciiart.eu/">ASCII Art archive</a>.

## Wrapping Up
Using certain characters and preserving whitespace can be a bit of a pain in HTML. However, by leveraging some of the concepts above, you do most things you would expect to be able to do.

Also, at this point in the sessions, you should have a good enough understanding of HTML to be able to display most content. In a future section, we'll learn some more advanced HTML concepts like tables, forms, and metatags. However, before we go there, we'll start learning how to make your HTML content pretty using CSS. 


