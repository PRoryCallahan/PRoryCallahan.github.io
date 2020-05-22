---
layout: post
title:  "Liquid Minutes"
date:   2020-04-27 20:06:06
categories: [coding, elachista]
author: Patrick Callahan
---

I fixed the estimated reading time issue the other evening, but Sunday suspended all work on the site. During this (hopefully, brief) interruption to Sunday services, I have worked up some responsive pages for displaying an order of prayer designed by the chief liturgist in our archdiocese. In some ways, it's been nice to have someone depending on my ability to push a snippet of code each week, even if it's the repetitive task of taking a Word doc and put it in markdown & html. I like the template too, so you might check it out [here](https://schoolofhope.github.io/).

It's a minor rabbit hole to add estimated reading time, but it's about eating the elephant one bite at a time. There are plug-ins for Jekyll that could be added to my `config.yml` file with appropriate indicators in my `post.html` or `_includes` files to add an estimated reading time to posts.

Still, plug-ins have to be maintained and for something as simple as this, I wanted to just build the command into the template without any dependency on someone else maintaining their gem file. So without further ado:

***

## Adding an Estimated Read Time to a Jekyll Blog

I knew I wanted to use a [Liquid variable](https://shopify.github.io/liquid/tags/variable/). Deciding on the best way to do this lead me a number of different examples of what others had done. But this example by [David Capello](https://davidcapello.com/blog/tips/reading-time-in-jekyll/) ended up being the shortest solution to my problem.

And it looks like this:

![minute code](/img/posts/2020-04-27-Liquid-Minutes/read_time.png)

There are lots of places where I could have thrown the code, but since it displays with the date and author, I thought it best to keep it on my Minima-inspired theme in the `post.html` file. N.B. I need to edit the `post.html` file because of how layouts work in Jekyll (and elsewhere). I won't rehash [layouts](https://jekyllrb.com/docs/step-by-step/04-layouts/) here. Perhaps another time.

But since this is intended as a dummies guide, here is how Capello's Liquid variable works:

1. `capture` captures the string inside the opening and closing of its tag and assigns it a variable, here `read_time` is my variable for everything between `capture` and `endcapture`

2. `page.content` is our liquid object.

3. `| number_of_words` is the first filter that manipulates the object. Here, it reduces the page content to its number of words.

4. `divided_by: 180` takes that number and reduces it a number of minutes. 180 wpm (words per minute) is a standard for read time on screens. (You can adjust the read time by simply changing the number. Most keep the number between 180 and 300 wpm)

5. Next, we need to round all returns of 0 mins up to 1 min. This requires an [if statement](https://shopify.github.io/liquid/basics/truthy-and-falsy/) in liquid. Specifically `if read_time != '0'`

6. And an [else statement](https://shopify.github.io/liquid/basics/truthy-and-falsy/) to make sure that 1 shows up.

7. Then wrap it all up inside html.
