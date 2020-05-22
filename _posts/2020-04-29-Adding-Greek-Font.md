---
layout: post
title: "Adding a Greek Font to Style Sheets"
date: 2020-04-29 14:00:00
categories: [coding]
author: Patrick Callahan
---
*N.B. (5/19/20) Update: the SCSS for Greek font is now stored in /custom/includes/_language.scss and is imported in /css/main.scss*

Before I tinker with any changes I want to make to font families for the Latin alphabet, I wanted to emend the Greek output in the style sheets.

But first let's take a look at Minima's font families:

<div class="no-select-button">
{% highlight scss %}
$base-font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol" !default;
{% endhighlight %}
</div>

For those unfamiliar with font families, the style sheet ranks fonts that the browser can display. Those viewing your page will either:

1. have to have the font stored locally,

2. be directed to a file for the font within one of your own folders,

3. or be directed to an external url that hosts the font (this is requires an extra step in your header that I'm not going to describe today)

Minima prefers <strong>system fonts</strong>. It first assumes the user has a mac: `-apple-system`. Then we go with Windows: `"Segoe UI"`. Then Android: `Roboto`. Then a laundry list of sans-serif fonts all the way down to `!default` just in case someone is operating some custom OS that uses none of the above.

I might go back and eventually develop Elachista to have only a single font family for all styles with a similar list of fall backs that are second-bests to the preferred font. But for today, I just wanted to designate a particular font for displaying Greek text and since most operating systems for American devices don't come loaded with fonts optimized for polytonic Greek, I am going to store the font in my `/assets/fonts` subfolder. Don't worry, today's font, [New Athena Unicode](https://classicalstudies.org/publications-and-research/nau-download), is released under an Open Font License so it's free to use so long as I'm not altering it without note or profiting from its distribution.

To designate a particular font for Greek, I'll make a css selector for Greek (grc) in my `_base.scss` file. It looks something like this:

##### _base.scss
{% highlight CSS %}
/**
 * Greek-Font
 */
 :lang(grc) 	{
    font-family: "New Athena Unicode", serif;
    src: url("/assets/fonts/newathu5_5.woff");
    font-size: 120%;
    }
{% endhighlight %}

If you're doing something like this on your own, you don't need to include the comment `/**Greek-Font*/`. I just kept the Minima template style of adding comments in the file so that it simplifies the process for tyrones to come along and personalize the theme later.

Even still, this designation will not automatically detect the language I am using on a particular page or post. On the particular page or post, I have to style my html or xml accordingly to mark that text section as Greek.

This can be done [multiple ways](https://www.w3.org/International/questions/qa-css-lang), but for html, one of the simpler methods is simply to use a `span` tag. An empty one would look like this: `<span lang="grc"></span>`. Just to make it clear, here is a comparison sample of html with and without the span tag:

<div class="no-select-button">
{% highlight HTML %}
Here is something Greek without html language styling: μηδὲν ἄγαν.

And here is something Greek with language styling: <span lang="grc">μηδὲν ἄγαν</span>.
{% endhighlight %}
</div>

And the result of each can be seen here:

Here is something Greek without html language styling: μηδὲν ἄγαν.

And here is something Greek with language styling: <span lang="grc">μηδὲν ἄγαν</span>.
