---
layout: post
title:  "Minute Counts & Images"
date:   2020-04-25 20:56:06
categories: [coding]
author: Patrick Callahan
---

About a year ago I began and quickly ended an experiment in creating introductory tutorials for Classicists looking to get into coding.

While I would like to add that to this site's portfolio, what I am intending to do for now is document in the blog what languages I used and link to recommended resources.

Today, I finally sat down with the [markdown cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) and stopped relying on my html knowledge. (In a future post or in a tutorial I will review how Jekyll posts work and what is required to know, i.e. markdown, and what is useful to know to get more out of posts, i.e. hmtl, yaml, css, sass, etc.). I went back to the [first post](/posts/2020-04-23-Midas-barber.markdown) and added an image of the judgement of Midas. At first I was looking to make it a header image to span the top of the post, but that is going to take a bit more tinkering with the layout of posts to format that correctly. How do I usually insert an image with html?

<div class="no-select-button">
{% highlight HTML %}
<img src="Midas-Judgement.jpg" alt="The Judgement of Midas">
or
<img src="url" alt="The Judgement of Midas">
{% endhighlight %}
</div>

You don't need `alt="..."` but if for some reason the image fails to load you aren't leaving your viewer in the dust.

What about markdown?

<div class="no-select-button">
{% highlight markdown %}
![Judgement of Midas](/images/posts/2020-04-23-Midas-barber/Midas-Judgement.jpg)
or
![alt text](url)
{% endhighlight %}
</div>

***

I also began working on figuring out how to code my own reading time estimates. It's a feature I first enjoyed on Medium and have also toyed with a few Jekyll themes that had this feature already loaded into it's blog templates. As with the images, this required me to actually dig into something I had been using but hadn't really mastered: [Liquid](https://shopify.github.io/liquid/).

But it's getting late and I don't want this blog to be a chore in itself so I'll save that for tomorrow. I'll have finished changes to my `post.html` in the interim so I will (hypothetically) have fixed the display of estimated reading time into the header of the posts by that time as well.
