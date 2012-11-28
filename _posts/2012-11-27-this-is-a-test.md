---
layout: post
title: This is a test
---

## {{ page.title }}

Of GitHub pages. 

Edit: Cool, it works! Here's what I did

* Created a repository named "mumrah.gitub.com" (replace mumrah with your username)
* Instead of using the page generator, just go copy the files from https://github.com/mojombo/mojombo.github.com
* Replace all of mojombo's info with your own ("Tom Preston-Werner" -> "Your Name", "mojombo" -> your username, etc)
* Create a test post (like this one)
* Push your master branch, and GitHub will build your static site!

I really like the idea of having control over your content like this. No complicated SQL database with "posts" and "categories" and "tags", just simple generated HTML.

Here is the test post I used:

<pre>
---
layout: post
title: This is a test
---

## {{ page.title }}

Of GitHub pages. 
</pre>

Name the file `_posts/YYYY-mm-dd-some-title.md` and it will get translated into a page at http://username.github.com/YYYY/mm/dd/some-title.html. 

Edit 2: Testing an image

![SIPI Jelly Beans](/images/SIPI_Jelly_Beans_4.1.07.jpg "SIPI Jelly Beans")
