---
layout: post
title: LaTeX, AdSense, and self-promotion
published: false
---

## {{ page.title }}

A few weeks ago, I was enlisted to write an article for [Software Developer's Journal](http://sdjournal.org/)
on Hadoop. I wrote a fair bit of source code for the article that I wanted to include as inline listings. The
specifics of the article aren't important (I'll talk about it later maybe), and that's not what we're here to 
talk about anyways (see title).

As part of delivering my article, the editor wanted images of my source code - as in screenshots. How awful, 
I thought, but I am of the mind that if you're going to do something, you may as well do it right.

This brings us to the LaTeX and the "listings" package. LaTeX is a document markup language and typesetting
system commonly used in academia. You give it some funky looking markup, and it gives you really nice looking
documents (pdfs and the like). The listings package enables you to make nice looking vector graphics from your
source code listings.

![LaTeX Listings image](/images/hello.png "Hello, LaTeX!")

Instead of crummy screenshots of Vim, I spent an afternoon getting texlive installed on my laptop and fiddling 
around with the settings. Before long, I was getting some nice looking PNGs of my source code listings. 

![Java source code listing](/images/listing-6.png "NGramWithIntWritable, yo.")

That's when I had the bright idea to make it into a web app

http://source2image.info

The whole thing took about 4 hours from idea to product, including provisioning a server on EC2, writing a Flask app,
and get LaTeX installed. I iterated on it for a few days and ran it by some colleagues before tossing up some 
AdSense ads and submitting to Reddit (Reddit quickly crushed my t1.micro, so I upgraded to a m1.large).

All told, I netted 9.36 with 1916 views and 13 clicks over three days. My CPC is up to 0.72 (which I think is pretty respectable),
and my page RPM is 4.88. All amounts are USD.

If only I could keep up that kind of traffic, this thing would pay for itself in no time. Too bad the need for images
of source code is pretty niche. That said, I am #3 for ["generate image of source code"](https://www.google.com/search?q=image+of+source+code).
Go ahead, click through to my site - you know you want to. I'm pretty sure the AdSense TOS forbids me from soliciting you to click on
any of my ads, so I'm not telling you to click on my ads.

Oh, and did I mention that I am keeping the code on GitHib. https://github.com/mumrah/source2image

## Links

* [My site, source2image](http://source2image.info)
* [Software Developer's Journal: Hadoop Issue](http://sdjournal.org/apache-hadoop-ecosystem/)
* [Wikibooks on LaTeX listings](http://en.wikibooks.org/wiki/LaTeX/Source_Code_Listings)
* [Official LaTeX docs](http://www.ctan.org/tex-archive/macros/latex/contrib/listings/)
