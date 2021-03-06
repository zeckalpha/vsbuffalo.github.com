---
layout: post
title: Hello, static blogging
---

# Why static blogging?

## Simplicity

I spend hours each week in Emacs, and I've spent [ages customizing
it](http://github.com/vsbuffalo/.emacs.d). With
[Jekll](http://github.com/mojombo/jekyll),
[Markdown](http://daringfireball.net/projects/markdown/syntax), and
[Blueprint](http://blueprintcss.org) I quickly built this site in my
favorite editor. I can spend time writing content, not fighting a
browser WYSIWYG editor.

## Mentality

Also, I want this site to function as a notebook. Most blogging
systems lead to a post-and-forget mentality. Revision control makes,
well, revisions easier.

## Plaintext

Plaintext is powerful (see [org-mode](http://orgmode.org/) if you
don't believe me). If I want to search all my posts using regular
expressions, I can with `grep`. How could this be done if I was using
WordPress or any blogging system that used database backend?

## Code-friendly

Jekyll plays well with [Pygments](http://pygments.org/), a Python
syntax highlighter. This is import because I want to share code. 

    {% highlight r %}
    # Jekyll is code friendly
    x <- seq(-1, 3, 0.1)
    y <- sin(x) + rnorm(length(x), 0, 0.3)
    plot(x, y)
    {% endhighlight %}

## Formulae

Initially I configured Jekyll to typeset formulae. However, Github
won't spend CPU cycles rendering everyone's LaTeX equations, so there
isn't a way to get formula rendering to play well with Github
posting. For hardcore math, I'll just share via PDF.

# My configuration

There's a myriad of Ruby tools and plugins for Jekyll - it's all a bit
intimidating. Here are a few notes on my configuration. [My
`_config.yml` file is definitely
important.](http://github.com/vsbuffalo/vsbuffalo.github.com/blob/master/_config.yml)

## Maruku and LaTeX
I am using the default Markdown parser, Maruku. Maruku has formulae
support, but it experimental and not on my default. Formulae are very
important to my notebook, so getting them to work is paramount. Here's
how I did it:

  1. Add the Maruku configurations below. Note the trailing slashes -
  these are important (and a sign that LaTeX support is still a bit
  rough.)

    maruku:
      use_tex: true
      use_divs: true
      png_engine: blahtex
      png_dir: images/latex/
      png_url: /images/latex/

  2. Install Xerces-C. On a Mac with MacPorts, use `sudo port install
  xercesc`. This is a requirement for `blahtexml`, which Maruku uses.

  3. Install `blahtexml`. Get the source at
  <http://gva.noekeon.org/blahtexml> and on a Mac, use `make
  blahtex-mac` and put this binary in `/usr/local/bin/` or some other
  place in your `$PATH`.


