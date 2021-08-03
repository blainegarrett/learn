# Session 4: Links and URLs


## Overview
In Session 2, we introduced one of the foundational elements of Hypertext: the `a` tag. In Session 3, we introduced how to embed various types of content within HTML. Both links and embedded content require a URL to link to or to embed. 

In this session, we will learn about what a URL is how it works as well as some tricks you can do.
<br />
<br />

### URLs and the Internet
At its core, the Internet is a whole bunch of computers connected together through a massive <s>series of tubes</s> network. Your computer, your phone, and your smart fridge are all part of the Internet. Also part of the Internet, a big part actually, are computers that serve up content - webpages, video, music, etc. These are called *servers*. When you view a webpage, you are making a series of *requests* for content on a server. These bits of content all have unique addresses on the Internet. This unique address is called a *URL* which is short for *Uniform Resource Locator*. 

<br />
<br />

## Understanding How URLs Work
### Phone Number Analogy
URL's have a consistent structure much like a phone number. A phone number in the US is 10 digit number that has three distinct parts. Take the phone number `612-0019-5829` as an example: 

- `612` is the *area/city code* that targets the part of the country
- `0019` is the *central office/exchange* code that targets things further
- Finally, `5829` is the *line number* that targets the specific phone subscriber

Each part of the phone number gets more specific until we get to the specific phone subscriber.

<br />
<br />

### Parts of a URL
Similar to a phone number, a URL is made up of several parts. Each part has a specific purpose to help target a specific piece of content on the Internet.


<img src="./url_parts.png" style="width:100%"/>

- **Protocol:** Establishes the request type with the most common being *http://* and *https://* which designates that the request is secure. Note: http stands for *hypertext transfer protocol*. This is also known as the *scheme*. We'll explore scheme's more below.
- **Domain:** The globally unique identifier for the website or server. This can be a domain name or IP address. 
- **Subdomain:** An optional prefix to the domain to further target content or request type. A common subdomain you may encounter is *www* which is usually dedicated to web trafic.
- **Path:** The location of the requested content on the domain. This may have a file extension associated with it depending on the type of content or how the server is set up.
- **Query** The question mark (*?*) after the path designates that there are additional information to be passed to the *path*
- **Parameters** An optional set of key/value pairs of strings passed to the path.
- **Fragment**
An identifier within the content that we want to specifically link to. This is useful for linking to other content within the same page (eg. a Table of Contents).
<br />

### Absolute & Relative URLS
A URL is an *absolute URL* if the entire URL and path can be pasted into a browser's address field to locate a specific page on the Internet. An absolute URL specifies the protocol, domain name, and often a subfolder or specific file name is included as well. This is the kind of URL you share on social media, send via email, etc. 

A relative URL specifies a path relative to the current URL. The protocol, domain, and subdomain are all inferred by the browser.

**Example:**
Assume we have a html page at 'http://www.example.com/book/intro.html' with the following link:
> `<a href="page2.html">next page</a>`
When the link is clicked, the browser will look for a html file at `http://www.example.com/book/page2.html`.

More examples. Can you guess what they do?
- `./page2.html`
- `../page2.html`
- `../book/page2.html`
- `/book/page2.html`
- `/`

Note: This is really only useful within HTML documents. You wouldn't, for example, share a relative URL on social media. 

<br />
<br />

## Some gotchas
Relative URLs allow us to leave off some critical parts of the URL. However, we can't pick and choose which parts to leave off. Here are examples of URLs that don't work as expected:
- `<a href="www.google.com">bad</a>` - no protocol
- `<a href="www.google">bad</a>` - no protocol nor TDL
- `<a href="http:www.google.edu">bad</a>` - Missing *//* in protocol

Note: If you paste some of these URLs into the browser URL bar, they might actually work. This is because the browser will try to resolve the issues to get you to the intended URL. Don't let that fool you however, these links will not work.

<br />
<br />

### Internal Links
As shown previously, you can create a link with an `a` tag with a `href` attribute with the value of a URL. Above we introduced the idea of relative and absolute URLs. There is one more type of URL worth discussing here: an internal link. Internal Links are links to a specific spot within a piece of content. This can be achieved by leveraging the *fragment* introduced above. You can use fragments with absolute urls, relative urls, or even on their own. 

Example:
> `<a href="#Overview">fragment only</a>`
This renders like: <a href="#overview">jump to overview</a>

This works if there is:
- an HTML element with an `id` attribute with the value of `overview` 
- an `a` tag with a `name` attribute with the value of `overview`

This last bit reveals why the tag is named `a`. The *a* stands for *anchor*. Internal links using anchors are the original usage of `a` tags. 

<br />
<br />

### Magic Links
You can do more with HTML anchor tags than just link to other html content. Using a variety of different *schemes*, you can do a variety of different things - such as dial a phone number or open an external application. [Here is a full list of schemes](https://en.wikipedia.org/wiki/List_of_URI_schemes). However, here are a list of practical schemes:

- **mailto** opens an application to draft an email to the target recipient `<a href="mailto:me@example.com">mail me</a>`
- **tel** opens an application to dial a phone number (phone app, Facetime, etc) eg: `<a href="tel:555-555-5555">call me</a>`
- **maps** opens an application to load a map with the target address `<a href="maps:q=Gamut+Gallery,+717+S+10th+St,+Minneapolis,+MN">Gamut</a>`

Note: As described above, the *http* and *https* protocols are also types of *schemes*. However, the structure of everything *after* the scheme is specific to the scheme. re: paths, fragments, etc may not work like they do with the URLs above.

## Wrapping Up
We now have a better understanding of how URLs work and different uses for the `a` tag.