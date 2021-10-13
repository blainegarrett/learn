# Session 8: Positioning


## Overview
Now that we have learned the box model, we will learn how to position the box on the page.

<br />

# Technique 1: Floats
One way to position HTML elements relative to each other is to use the `float` declaration. In combination with the `clear` directive, elements can visual columns of content. 

Example:
```
<div style="border: 1px solid #cccccc">
   <img src="pineapple.jpeg" style="width:50%; float:left;"/>
   <div style="float:left; width: 50%">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus imperdiet, nulla et dictum interdum, nisi lorem egestas odio, vitae scelerisque enim ligula venenatis dolor. Maecenas nisl est, ultrices nec congue eget, ...
   </div>

   <div style="clear:both"></div>
</div>
```

<div style="border: 1px solid #cccccc">
   <img src="pineapple.jpeg" style="width:50%; float:left;"/>
   <div style="float:left; width: 50%">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus imperdiet, nulla et dictum interdum, nisi lorem egestas odio, vitae scelerisque enim ligula venenatis dolor. Maecenas nisl est, ultrices nec congue eget, ...
   </div>

   <div style="clear:both"></div>
   <div>Content After the float</div>
</div>


This *was* a common way to create website layouts in the early 2000s, but they tended to be very fragile. It is more commonly used these days for positing content, such as in the example above. Since `float` only deals with horizontal positioning, it is not super useful in som cases.

<br /><br />
# Technique 2: Absolute and relative positioning
To have more control over horizontal and vertical positioning, we can use the `position` directive. Elements are positioned using the `top`, `bottom`, `left`, and `right` directives. Depending on the value of the `position` directive, the elements will be globally (absolutely) or relative to their parent.

Example:
```
<div style="border: 1px solid #cccccc; position: relative;">
   <img src="pineapple.jpeg" style="width:50px; position: absolute; bottom:10px; right:10px"/>
   <div style="width: 50%">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus imperdiet, nulla et dictum interdum, nisi lorem egestas odio, vitae scelerisque enim ligula venenatis dolor. Maecenas nisl est, ultrices nec congue eget, ...
   </div>
</div>
```

<div style="border: 1px solid #cccccc; position: relative;">
   <img src="pineapple.jpeg" style="width:50px; position: absolute; bottom:10px; right:10px"/>
   <div>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus imperdiet, nulla et dictum interdum, nisi lorem egestas odio, vitae scelerisque enim ligula venenatis dolor. Maecenas nisl est, ultrices nec congue eget, ...
   </div>
</div>

<br />
In the above example, the image is absolutely positioned to the bottom/right of the parent `div`. Since the parent `div` is relatively positioned, the absolute positioning is relative to the parent vs. globally positioned. 

🧠 Try removing the parent's `position: relative` declaration and figure out where the image went to. (hint: scroll up)

# Technique 3: Box Model
We'll save this for next session.



## Homework
1. Create a small gallery of thumbnail images using the float property. Use an HTML ordered list with list elements containing images. 

2. Add a tool tip to one of the thumbnails that describes what is in the image. The tooltip should only show when the thumbnail is moused over. Hint: This will require the `:hover` psuedo selector and absolute positioning.


