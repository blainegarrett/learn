# Session 7: Block Elements &amp; Box Model


## Overview
Now that we have a basic understanding of CSS declarations, we're going to learn how HTML elements occupy space.

<br />

# Inline vs. Block
In session 2, we hinted that certain HTML elements are considered "block" elements and certain elements are considered "inline" elements. Elements such as `b`, `q`, `span`, are *inline* elements in that they appear inline with other content - that is to say, they do not create their own line break and are only as wide as the containing content. Whereas, a `div` or `blockquote` are *block elements* that will fill the available width and push down other content. Inline elements should not contain block level elements. It may not work as expected.

An element being an *inline* or *block* level element is more than just visual display. Using the construction analogy, we can paint a piece of styrofoam to look like concrete, which might be fine for a theater set, but we wouldn't want to use it for a building's foundation.


### Controlling display with CSS
We can use CSS to control the visual display of elements. We can make an inline element display like a block element and vice versa. This is done via the `display` directive. 

Given the following HTML, we can make a `span` display like a block element:

```
<div>This is a <span class="block-test">span</span> element</div>
<style>
.block-test {
   border: 1px dashed red;
   display: block;
}
</style>
```


<style>
   .block-test {
      border: 1px dashed red;
      display: block;
   }
</style>

> <div>This is a <span class="block-test">span</span> element</div>

<br />
Similarly, we can make a block level element display like an inline element.
<br />

```
<div>This is a <div class="inline-test">div</span> element</div>
<style>
.inline-test {
   border: 1px dashed red;
   display: inline;
}
</style>
```


<style>
   .inline-test {
      border: 1px dashed red;
      display: inline;
   }
</style>

> <div>This is a <span class="inline-test">div</span> element</div>

<br />

### Inline Blocks
Remember, inline elements display inline with content. Their width, height, etc are controlled by their containing content. Sometimes, it is ideal to have an element be *inline* but be able to have defined height and width, etc. This is where the *inline-block* comes in. It combines the best of both worlds.



```
<div>This is a <div class="inline-block-test">div</span> element</div>
<style>
.inline-block-test {
   border: 1px dashed red;
   display: inline;
}
</style>
```

<style>
   .inline-block-test {
      border: 1px dashed red;
      display: inline-block;
      width: 150px;
      text-align: center;
   }
</style>

> <div>This is a <span class="inline-block-test">div</span> element</div>





### Other display values
The `display` directive has a number of allowed values. We'll cover some additional options in later lessons. However, one useful value is `none`; When the browser processes this directive, it will visually hide the HTML element and all of its children.



```
<div>This is a <div class="hide-test">div</span> element</div>
<style>
.inline-block-test {
   border: 1px dashed red;
   display: none;
}
</style>
```

<style>
   .hide-test {
      border: 1px dashed red;
      display: none;
   }
</style>

> <div>This is a <span class="hide-test">div</span> element</div>

<br />

* Note: The `div` is magically gone.

<br />
<br />

### The Box Model
A block element (or an inline element with `display:block` or `display:inline-block`) follows the *box model*. It is a conceptual model of how the element consumes space. 

<br />
The box model:
<br />
<img src="./boxmodel.jpeg" />

- *Content:* This is the text and HTML content of an element. It consumes height and width. 
- *Padding*: The amount of whitespace to surround the contents of the box.
- *Border*: The conceptual boundary the separates "inside" the box and "outside" the box. 
- *Margin*: The whitespace outside of the box separating it from other boxes.

<br />

*Shipping Analogy*: Pretend you are shipping something fragile to a relative. The fragile item is the *content*. You wrap it in bubble wrap to protect it. This is the *padding*. Then you put it in a box. This is the *border*. Finally, you might shrink wrap the whole thing in additional packing to keep it extra safe. This is the *margin*. Finally, you slap a label on it and that is now your shippable package. The entire package *is* the thing being shipped and counts towards the overall weight, dimensions, and shipping cost. Conversely, you can skip all the packaging (such as in the case of a <a href="https://uspsblog.com/mailing-coconut/">Post-a-Nut</a>.


Example:
<br />


```
<style>
   .box-example1 {
      text-align: center;
      padding:50px;
      margin:50px;
      border: 1px solid red;
   }
</style>
<div class="box-example1">Content</div>

```


<style>
   .box-example1 {
      text-align: center;
      padding:50px;
      margin:50px;
      border: 1px solid red;
   }
</style>
<div class="box-example1">Content</div>



### Targeting specific "sides"
Like a normal rectangle, the box model has four sides - top, right, bottom, left. In the example above, each of the directives implicitly applied its value to all four sides uniformly. We can also be more explicit.

If you provide 1 value, the value is uniformly applied to each side.

<br />

```
padding: 5px
```

<style>
   .side-demo {
      display: inline-block; border: 1px solid red;
   }
</style>
<div class="side-demo" style="padding: 5px">content</div>

<br />

If you provide 2 values, the first is applied to the top and bottom. The second is applied to the left and the right.

<br />

```
padding: 5px 20px;
```
<div class="side-demo" style="padding: 5px 20px">content</div>

<br />

If you provide 4 values, you can specifically target each individual side in order of: top, right, bottom, left

<br />

```
padding: 5px 10px 20px 30px
```
<div class="side-demo" style="padding: 5px 10px 20px 30px">content</div>


<br />
<br />
You can also leverage *cascading* to tweak a specific side:

```
border: 1px solid red;
border-left: 5px dashed blue;
```

<div class="side-demo" style="padding: 10px; border: 1px solid red;
border-left: 5px dashed blue;">content</div>


### Takeaways
HTML elements consume space. How they consume space is determine if they are displaying inline or as a block element. This can be controlled via CSS. Also, elements follow the *box model* and can be highly customized through CSS.

<br />

## Homework
Recreate the <a href="./boxmodel.jpeg">diagram above</a> using nested divs with colored backgrounds and borders. Utilize padding and margin to create the visual space. 

