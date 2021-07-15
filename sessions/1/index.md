# Session 1: Introduction to HTML Part 1

## 1. What is HTML?
*HTML* is the standard language for displaying most content on the Internet. It is used to create everything from simple text formatting to complex forms. It is a fundamental building block of content on the Internet. 

HTML stands for *Hyper Text Markup Language*. As a "*markup language*", HTML is a set of instructions to tell a program (such as a web browser) how to interpret text and other content. It also allows the web browser to know a variety of other things about the content in order to support voice browsers, social sharing, and more. 


### What HTML *Isn't*?
Before digging in, let's clarify what HTML is not:

- Images, audio, nor video content are not HTML. However, HTML can be used to display these things. 
- HTML is not a programming language. However, a lot of web development involves using programming languages to generate HTML content.
- In most cases, HTML should not be used for formatting content. Things like font formatting, colors, animations, etc are left up to CSS, which will be covered in Session 3.

**Takeaway:** HTML is a standardized language for displaying content on the web. 

---

## Section 2. The Basics
The absolute foundation of HTML is the *Element*. HTML elements are often called HTML *Tags*) and the terms may be used interchangeably.

Elements can wrap text or other elements to give them meaning. It is common lingo is to refer to the contents of an element as *children* with the element being the *parent* of the *children*. These child elements can, themselves, contain text or other elements. 

**Example:**
```
<parentTag>
   Text Child
   <childTag>GrandChild Text</childTag>
</parentTag>
```
In the above example, `parentTag` contains two children: one block of text and one `childTag` which in turn contains a block of text.


Note: Don't read too into the parent/child metaphor. Children have at most one parent and we rarely talk about things in terms of grandparents and even less so cousins, etc.

As illustrated in the example above, HTML tags have an *opening* tag and a *closing* tag in order to wrap its children. The exception to this is when there are no children, which we will see in later examples. 

**Takeaway:** HTML is made up of a hierarchy of tags. Tags use opening and closing tags to wrap its children.


---

## Section 3. Semantic Meaning
There is a standard set of HTML tags. These are defined by an organization conceptually similar to the ones that define building codes or standard paper sizes. These standards change over time, but for the most part web browsers keep up to date with the latest standard.

Each HTML tag has a specific purpose in life. There are tags to embed an image or video. There are tags to make lists of things. There is even a tag to quote something. There are many tags, but each has a specific purpose.


**Example:**
The `h1` tag is used to designate it is a 1st level heading.
```
<h1>Important Heading</h1>
```

In the "olden days" prior to the invention of CSS, there were tags for visual formatting (such as the `font` tag and the dreaded `blink` tag). However, as the internet has evolved, the purpose for HTML has shifted away from formatting and more towards semantic meaning, which is a fancy way to saying that an HTML tag describes what it's contents *are* rather than how they *look*. 

That said, web browsers often interpret the semantic meaning of the tag and will apply visual formatting. 

For example, the browser will visually render a `strong` tag with a bold font. 

```
<strong>This text is bold</strong>

is rendered as:
```
**This is bold**

Similarly, the following is an `unordered` list:
```
<ul>
    <li>First Item</li>
    <li>Second Item</li>
</ul>
```
Most browsers will render this as a nice visual bullet list:
* First Item
* Second Item


**Takeaway**
There are lot of different HTML tags - each with their own defined meaning.


---
## Section 4: Attributes
HTML attributes provide additional information about HTML elements. They always appear on the opening tag and they always come in name/value pairs in the form `name="value"`.


**Example**
Let's pretend we have a `person` element. We might then provide an attribute to define the person's age.
```
<person age="39">...</person>
```
Note: There is no person tag defined in the HTML standard. This is just for illustration purposes.

There are many types and purposes for them. Some attributes only apply to specific elements while some attributes can apply to many elements. Some elements even have required attributes.


**Example:**
Browsers will render an image when they interpret an `img` tag. However, there needs to be an `src` attribute to tell the browser *which* image to display.

```
<img src="https://lorempixel.com/400/200/animals/4/" />
```

Most browsers will display:
![](https://lorempixel.com/400/200/animals/4/)


Note: The `src` attribute is specific to the `img` element (and a select few other elements). However, putting an `src` attribute on a `h1` header element doesn't make sense. 

Note: Unrelated to attributes, notice that the `img` doesn't have any children unlike the other HTML elements we have seen so far.

**Takeaways:** HTML attributes are sometimes optional and sometimes required by HTML elements. However, they are always in the form of `name="value"`.


## Wrapping Up
In this session we learned about the basic structure of HTML elements. In the next session, we will introduce some of the most commonly used HTML elements.
