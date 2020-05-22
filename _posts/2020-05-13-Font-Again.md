---
layout: post
title: "Back to Fonts"
author: Patrick Callahan
date: 2020-05-13 20:30:00
category: [coding]
---
*N.B. This is from before I re-booted the theme and needs to be updated (5/19/20)*

I kept at it building the other tutorials and took notes for a different kind of tutorial to try to do a step-by-step of building an API to serve JSON texts.

But just to have something done for the end of the day, I logged on as I try to make sure the kids go to sleep and finally altered Minima font families to distinguish between the base font and the heading font. I wanted to try a serif font family for the body so I altered `$base-font-family` in `elachista.scss` to read: `"Palatino Linotype", "Book Antiqua", Palatino, serif;`. I will eventually upgrade the first option font, but it's a good place holder for now.

I then added the following lines to `elachista.scss`:

```scss
$heading-font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol" !default;
$heading-font-size:   16px !default;
$heading-font-weight: 400 !default;
$heading-line-height: 1.5 !default;
```

So now I have a `$base-font-family` variable and a `$heading-font-family` variable. But that doesn't do me any good unless I style some applications of those variables. This means going into `_base.scss` and cheching on body and heading font families. I didn't have to do anything for body text, but I did have to jump down to headings and re-style it thus:

```scss
/**
 * Headings
 */
h1, h2, h3, h4, h5, h6 {
  font-family: $heading-font-family;
  font-weight: $heading-font-weight;
}
```

Save everything, reload the local build, and ecce! we now have two font-families being served depending on the typographic hierarchy.
