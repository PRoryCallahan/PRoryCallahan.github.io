---
layout: post
title: "Centering"
date: 2020-04-28 14:00:00
categories: [coding]
author: Patrick Callahan
---
*N.B. This is from before I re-booted the theme and needs to be updated (5/19/20). Moreover, Bootstrap centers the image by default so it is no longer necessary.*

Small step today: modified `_base.scss` to horizontally align images

Original theme:

##### _base.scss
{% highlight SCSS %}
img {
  max-width: 100%;
  vertical-align: middle;
}
{% endhighlight %}

Now I've added a class of `img` below in `_base.scss`

##### _base.scss
{% highlight SCSS %}
img.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
{% endhighlight %}

<img src="/img/posts/2020-04-23-Midas-barber/Midas-Judgement.jpg" alt="Judgement of Midas" class="center">

I could have just modified `img` rather than add `img.center` but I wanted to keep the original style as the standard and centering only as a variation.
