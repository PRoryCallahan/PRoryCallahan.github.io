---
layout: post
title: Pythika, a Python-powered Gnome Generator
author: Patrick Callahan
description: 'Learn how to generate a CSV file <br />and the basics of Python from the Pythia'
image: assets/images/pic07.jpg
---
Pythika is a brief introduction to Python for Classicists...

## What you will make

The Pythia's Gnome Generator is based on the principles behind the various <a href="https://projects.raspberrypi.org/en/projects/shakespearean-insult-generator">Shakespeare Insult Generators</a> that have been floating around for a few years. While this tutorial focuses on Python, I was first introduced to the principles behind such generators in a <a href="https://apps.apple.com/us/app/shortcuts/id915249334">Javascript version</a> that ran as a widget on my iPhone so I could insult from my lock screen. But long before this, the principles behind these have been a staple of some popular internet apps (e.g. once upon a time there was a high school poetry generator that was popular in the early 2000s).

## A ΓΝΩΜΗ is not a GNOME is not a Gnome is not a gnome.

No, the Pythia's Gnome Generator will neither produce gnomes for your D&D game nor the garden variety for your lawn. And as much as I like Linux, it will not produce a <a href="https://en.wikipedia.org/wiki/GNOME">GNOME desktop environment</a>.

A gnome (<span lang="grc">γνώμη</span>) refers in the poetry of Pindar to a kind of maxim or short wisdom statement. The standard ancient definition can be found in <a href="http://www.perseus.tufts.edu/hopper/text?doc=Perseus%3Atext%3A1999.01.0060%3Abook%3D2%3Achapter%3D21%3Asection%3D2">Aristotle's <i>Rhetoric</i></a> and if you really want to dig deep you can read my friend Michael Boler's <a href="https://fordham.bepress.com/dissertations/AAI3466695/">dissertation on gnomes in Bacchylides</a>. Since they are short and self-contained, they are an ideal sample set for a random line generator.

## What you will learn

<ul>
	<li>How to Read and Write a CSV (Comma Separated Values) file</li>
	<li>How to Manipulate Lists</li>
	<li>How to Randomly Choose an Item from a List</li>
  <li>Create a Basic GUI (Graphic User Interface)</li>
</ul>


## What you will need

<dl>
  <dt>Hardware</dt>
  <dd>
    <ul>
      <li>Computer (PC/Mac/Linux)</li>
    </ul>
  </dd>
  <dt>Software</dt>
  	<dd>
      <ul>
        <li>Python 3 (<a href="https://projects.raspberrypi.org/en/projects/shakespearean-insult-generator/2">install instructions here</a>)</li>
        <li><a href="https://lawsie.github.io/guizero/">guizero</a> Python module (<a href="https://projects.raspberrypi.org/en/projects/shakespearean-insult-generator/2">install instructions here</a>)</li>
        <li>a text editor (You can use your default text editor, e.g. TextEdit in Mac, but you can also go even simpler by using a terminal editor like <a href="https://www.nano-editor.org/">Nano</a> or with more bells and whistles and use something like <a href="https://atom.io/">Atom</a> which I prefer for its integration with GitHub and its open-source philosophy. Later I'll put together a tutorial and page on text editors; for now, use what you are comfortable with as long as it is not MS Word, Google Docs, or any word processor)</li>
      </ul>
    </dd>
</dl>

### What is a CSV file?

A <b>C</b>omma <b>S</b>eparated <b>V</b>alues or <b>CSV</b> file is a text file where the contents have been sorted in a simple format, i.e. by commas. Here is an example:

A code section without any header
<div class="no-select-button">
{% highlight CSV %}
<span>Alcman, Sappho, Alcaeus, Anacreon, Stesichorus, Ibycus, Simonides, Bacchylides, Pindar</span>
{% endhighlight %}
</div>

We can also <i>encapsulate</i> values in our CSV, for example:

A code section without any header
<div class="no-select-button">
{% highlight CSV %}
<span>"Alcman", "Sappho", "Alcaeus", "Anacreon", "Stesichorus", "Ibycus", "Simonides", "Bacchylides", "Pindar"</span>
{% endhighlight %}
</div>

But why would we want to encapsulate? Because our values need not be one word, they can be full or partial sentences. And those sentences can include commas. Encapsulating helps Python distinguish between commas that separate values and commas that belong inside the value. For example:

A code section without any header
<div class="no-select-button">
{% highlight CSV %}
<span>"Homer, singer of tales", "Homer, the blind bard", "Homer, the Chian"</span>
{% endhighlight %}
</div>

There are two ways I would recommend generating a CSV file. For those more comfortable operating in a standard software, you could use Microsoft Excel, LibreOffice Calc, or even Google Sheets, type each value into a separate cell and then save/export the file as .csv. If you feel more comfortable in this environment, see this <a href="https://projects.raspberrypi.org/en/projects/shakespearean-insult-generator/5">Shakespeare Insult Generator</a> for step-by-step instructions.

But I would recommend this tutorial as an invitation to leave the relative safety of these software tools and start editing plain text. There are lots of ways to do this and I will discuss one option below as it was how I generated my own gnomes.csv file.

## Adding gnomes to a CSV file via plain text

For this tutorial, I read through <a href="http://www.perseus.tufts.edu/hopper/text?doc=Perseus%3Atext%3A1999.01.0162%3Abook%3DO.%3Apoem%3D1">Diane Svarlien's translation</a> (1990) of Pindar and just copied and pasted whatever gnomes took my fancy. You can download my pre-built <a href="https://github.com/PRoryCallahan/Pythika/blob/master/gnomes.csv" target="blank">gnomes.csv</a> if you just want to practice the Python coding, or if you are feeling adventurous, you can assign anything strikes your fancy as the values, for example, do you want to turn it into a Aristophanes Insult Generator, a Homeric Epithet Generator? Great. If you're a grad student who has a long list of reading to do for comprehensive exams and can't decide where to start, feed your authors/works into a CSV and let Python decide the order you prepare for comps (just be sure to delete read authors from your csv the next time you generate a selection!). If you're feeling really adventurous stick around and I'll show you how to craft a <i>Sortes Vergilianae</i> [<i>link to be added</i>].

### Populating your CSV with a Text Editor

*Editor note: These steps are still in draft. But necessary for those not comfortable opening Jupyter Notebook...which if you're learning basic Python should be the assumption.*

In this exercise, I will be showing you my own process with my text editor, <a href="https://atom.io/">Atom</a>.

<ul>
  <li>Open a new folder (on your desktop or where you please). Name it <i>Gnome_Generator</i> (or whatever you please). Then in Atom, go to <i>File</i>, click <i>Open</i>, navigate to your <i>Gnome_Generator</i> folder. Open a new file. Save as <i>gnomes.csv</i></li>
