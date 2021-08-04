# Session 3: Embedding Content

## Overview
In Session 2, we introduced some basic HTML for content. In that session, we introduced the `a` tag which is a big part of the magic of linking different chunks of HTML together to create the <b>🎺 WORLD WIDE WEB 🎺</b>. Another big part is the ability to embed other content into HTML like images, audio, and video.

In this session we'll introduce how to embed these types of content into your HTML and showcase some other common embed types you might run into in the wild.

## Before We Begin
### Accessibility Note
Voice Browsers typically cannot understand the contents of an image, audio file, or video file. Sometimes this content is critical and we need to clue in the browser to what the embedded content is. For example, an image that contains text might contain important information that the user needs. To get around this, we can add an attribute to indicate the meaning of the embedded content. Which attribute we use varies by the type of content we're embedding. These attributes will be called out below as we introduce each content type.

### Security
As your are experimenting with embedding content, you might run into security issues preventing the content from displaying correctly. We will cover a variety of security topics in a different section. However, check the developer console for security errors. Your browser may not let you embed content in certain cases and/or the content may not allow you to embed it. The later is known as "hotlinking" and many websites prevent you from embedding their content to save on bandwidth costs. 

Note: Github prevents the embedding of everything except for images. You will need to create a local HTML file for testing these in lieu of the playground on github.


## Embed types

### Images 
Images are the most common embed type. To embed an image into your HTML page, you will need to use an `img` tag with a `src` attribute. The value of the `src` attribute is the URL to an image file.

Example:
```
<img src="https://lorempixel.com/400/200/animals/4/" alt="An Animal" />
```

This will display as:
> <img src="https://lorempixel.com/400/200/animals/4/" alt="An Animal" />

<br />

**File Types**<br />
Only certain types of files can be embedded into HTML. The most common are:

- png (Portable Network Graphics)
- jpeg (Joint Photographic Expert Group image)
- gif (Graphics Interchange Format)
- SVG (Scalable Vector Graphics)

Newer image formats are developed all the time and you may run into them in the wild, however please note that browser support for these types may not be 100% yet. [View a full list of image file types](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Image_types).

Use the `alt` attribute to describe what is in the embedded image. 

<br />
<br />

### Audio
You can embed audio into your html content. Most browsers will render a simple player UI. 
```
<audio controls>
  <source src="https://www.learningcontainer.com/wp-content/uploads/2020/02/Kalimba.mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>
```


### Video
You can embed video into your html content. Most browsers will render a simple player UI. 
```
 <video width="320" height="240" controls>
  <source src="https://storage.googleapis.com/mplsart-cdn-central/junk/pexels-nadezhda-moryak-8678456.mp4" type="video/mp4">
Your browser does not support the video tag.
 </video>
```



### Iframes
In all the above examples, we have embedded non-HTML content, specifically "multimedia". You can also embed other HTML content.
This is accomplished via the `iframe` tag. 

```<iframe src="https://www.google.com"></iframe>```

<br />

### YouTube 
A common type of content you might have to embed in your HTML is a YouTube video. 

```
<iframe width="560" height="315" src="https://www.youtube.com/embed/02NQkhbjALg" title="YouTube video player"  allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
```




