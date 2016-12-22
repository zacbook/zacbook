---
layout: post
title: "Web Development Tips and Notes"
date: 2016-12-18T00:33:10-08:00
categories: Development
tags: html, css, jekyll, liquid, octopress, mathjax
excerpt:
---

In an attempt to learn more about HTML, CSS, and using Jekyll, I started creating [ZacBook.net](http://zacbook.net) from scratch. As [my previous projects](http://drz.ac) show, I clearly enjoy hacking blogs together over actually writing one. 

Along the way—usually after some Googling—I learned a few things. In no particular order, here are some of them that may be useful for others (or myself) in the future:

- In Jekyll (v. 3.3.1), posts by default do not receive a `post.title` YAML / Liquid variable. However, if one creates a posts `collection` in their `_config.yml`, then `post.title` will be set to the filename of the post (without the extension). This is important if one relies on `post.title` being empty before falling back to the default `site.title`. 

- Search engines typically truncate the `name="description"` HTML metadata at [160 characters](https://moz.com/learn/seo/meta-description). This is why many Jekyll templates employ the `truncate: 160` Liquid filter.

- If you want search engines to only list one version of your URL (say, without the index.html), take advantage of the [`rel="canonical' element](https://yoast.com/rel-canonical/).

- Some / older browsers indicate, usually through an icon in the address bar, that a site has an RSS or Atom feed. It's probably nice to take advantage of this using the [`rel="alternate" type="application/rss+xml"' element](http://www.femgeek.co.uk/typeapplicationrssxml-where-for-are-thou/), even though [RSS is dead](https://techcrunch.com/2010/09/13/rss-is-not-not-not-not-not-dead/).

- Many Jekyll themes add both `categories` and `tags` to posts or pages. While they may seem redundant, you can make good use of them through [their subtle different meanings](https://en.support.wordpress.com/posts/categories-vs-tags/). Punchline: `categories` can be used for broad topic groupings whereas `tags` can be used like keywords.

- One can use the [HTML5Shiv](https://en.wikipedia.org/wiki/HTML5_Shiv) to compensate for [Internet Explorer 8's limitations](http://www.w3schools.com/html/html5_browsers.asp). Just add
``` html
<!--[if lt IE 9]>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.3/html5shiv.js"></script>
  <![endif]-->
```
to your `head`. Along the same lines, even though [it's probably not required](http://stackoverflow.com/questions/6771258/what-does-meta-http-equiv-x-ua-compatible-content-ie-edge-do), stick 
``` html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```
in there as well, close to the top.

- Although you can put your CSS and JavaScript files anywhere, `/css/` and `/js/` seem pretty popular. One can also separate out project-specific versus general-purpose code, as detailed on [this StackOverflow post](http://stackoverflow.com/questions/24199004/best-practice-to-organize-javascript-library-css-folder-structure).

- While probably best handled via CSS, one should appropriately [set the viewport](http://www.w3schools.com/css/css_rwd_viewport.asp) to be friendly to mobile browsers. It's as easy as adding
``` html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```
to your `head`. Here's some [further elaboration](https://webdesign.tutsplus.com/articles/quick-tip-dont-forget-the-viewport-meta-tag--webdesign-5972).

- Even though I've known about [Liquid](https://shopify.github.io/liquid/) for several years. I didn't realize it was developed at [Shopfiy](https://www.shopify.com). Props to them!

- You can [configure MathJax to only process part of the page](https://github.com/mathjax/MathJax/issues/1218), see [this code snippet](http://jsfiddle.net/artur99/1erzqsy6/1/) for an example.

- The default [margin around the body of an HTML document is 8px](http://stackoverflow.com/questions/13127887/html-default-body-margin). If you're wondering why your CSS elements don't touch the edge of the browser window, this is why.

- If you care about CSS consistency across multiple browsers, [Normalize.css](http://necolas.github.io/normalize.css/) may be a good solution.
