---
layout: post
title:  "How to reference equations properly in Office (2013, 2016)"
date:   2017-03-27 09:59:59 +0100
categories: mypost
---
# Introduction

I haven't written anything for a long time. Sorry, my bad. However, I'm writing my PhD thesis these days and for some reasons I chose Microsoft Office to do that. Some might say, that TeX is much better, which is true in some sense. The main reason I chose Office is that I know it better, than the whole TeX system and I find much faster to type and format the material, even if it's not *that* pretty at the end. The figure and section references are work quite well. I cannot even say anything bad about the referencing system. In Office 2013 I can choose the IEEE form (which was not present in the earlier versions like Office 2010), which is the common referencing format in my field. So things changed for the better over the years.

But there is always a *"but"*. And this but is about the equation referencing. The common solution for the equation numbering is to use brackets and a number in between, like the following (I use [MathJax][mathjax] here).

$$ E = m \cdot c^2 $$

I found a good guide about how to number your equations correctly and automatically ([this one][office2016-eq-num]), however, the referencing were always a pain in the ass. After a long search, I found a quite good solution, but I hope, that the future versions of Office will deal about this problem. I think, it wouldn't require much effort from the developers. In the first round, I would be happy, if these steps were work automatically, in one step.

# How to do it?

As far as I know, these steps work for both Office 2013 and 2016 versions (as of now).

This is my first post, which is the edited example page from Jekyll. So I definitely will try the syntax highlight! :) First, with Python, because I use Python quite often. I am very curious, whether I have to do any more at GitHub or it will work out of the box.

So here is the Python code snippet, I hope it will work.

{% highlight python %}
def print_hi(name):
  print("Hi, {}".format(name))

print_hi('Tom')
# prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

And some useful pages below.

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[office2016-eq-num]: https://blogs.msdn.microsoft.com/murrays/2015/05/14/equation-numbering-in-office-2016/
[mathjax]: http://gastonsanchez.com/visually-enforced/opinion/2014/02/16/Mathjax-with-jekyll/
[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
