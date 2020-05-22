---
layout: post
title: "Elachista is Sassy"
date: 2020-05-08 14:00:00
categories: [coding, elachista]
author: Patrick Callahan
---
*N.B. This is from before I re-booted the theme and needs to be updated (5/19/20). None of this applies with the new Bootstrap build of Elachista, but may be helpful to those looking to build off Minima*

It's been a week without a post logged but several are in draft as I build out portions of the theme and toy around with the best way to leave bread crumbs, *micae panis*, for fellow Classicists, Digital Humanists, et al. to adapt Elachista to their needs.

But I'm happy to say that all files and commands now reflect the themes name. This may not seem like a big deal, but reviewing how I made the change might help other tyros understand:

1. Gem files in Jekyll pages
2. sass/scss/css imports

If you're planning on displaying texts and their attendant translations, it's foundational to understand style sheets so this post is a good place to review the frame of Elacista's style sheets.

**Moment of Honesty:** First, I tried, *and failed*, to surgically change a few settings without eliminating all of Minima--I didn't want to let go yet of the safety net of the automatic updates that Minima installs. But eventually I rolled up my sleeves and did the following:

## Gemfile

Minima is kept up-to-date via [rubygems](https://rubygems.org/). The `Gemfile` in Jekyll declares which gems Bundler uses to help build the theme. I don't want to erase the file altogether because it does useful things, such as storing plugins. So today all I did was inactivate the gem for Minima: `gem "minima", "~> 2.5"`

Whenever I release the theme officially, I will have to package the theme so that it too can be added to someone else's Gemfile. But not today.

## SASS/SCSS/CSS

For those tinkering around with the foundations of coding, you might have the basics of HTML and CSS, and then again you might have learned to code years ago before, say, HTML5 (2008) or CSS in a similar timeframe.

Since I loathe when others don't define terms, here's the no shame breakdown of those abbreviations (and please call me out when you see me not leaving such details):

CSS = <b>C</em>ascading <b>S</b>tyle <b>S</b>heets

SASS = <b>S</b>yntactically <b>A</b>wesome <b>S</b>tyle <b>S</b>heets

SCSS = <b>S</b>assy <b>C</b>ascading <b>S</b>tyle <b>S</b>heets

The advantage with Sass is that SCSS accepts CSS so, while SCSS probably has a cleaner, friendly way of doing X as SCSS, I can still compose X as I always did in CSS if I am more familiar with that or it just works better for my process and/or integrating with existing peripherals.

All of the work today is mostly a glorified 'find & replace' through various files, but those files have an order of dependency.

### main.scss

Originally `/assets/main.scss` read:

##### /assets/main.scss
{% highlight SCSS %}
@import "minima";
{% endhighlight %}

And as you might guess, it now reads: `@import "elachista";`

Next up:

### The Sass folder

Then I had to go into my `_sass` folder. First, I renamed `minima.scss` to `elachista.scss`. Then I renamed the folder `minima` to `elachista`. And this meant I had to review the files in my `_includes` folder to make sure that any reference to those style sheets now reflected their new path:

1. `/minima/base.scss` ===> `/elachista/base.scss`
2. `/minima/layout.scss` ===> `/elachista/layout.scss`
3. `/minima/syntax-highlighting.scss` ===> `/elachista/highlighting.scss`

### social icons

Finally, I had to go back to the `assets` folder and rename the social icon .svg file to `elachista-social-icons.svg` and check the `_includes` and `_layouts` files for any reference to `minima-social-icons.svg`. Then I updated them the same as I did for anything referencing the Sass folder contents.

Now, as the cliche goes, we're cooking with gas. So long Minima, hello Elachista.
