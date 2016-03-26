---
layout: post
title: "Markdown text for GitHub from HTML"
excerpt: "Yes, it's a round-trip ticket"
tags: [HTML, personalization, jekyll]
image:
  feature: pic rainbow splash black apple logo 1900x500.jpg
  credit: Brothersoft
  creditlink: http://m.img.brothersoft.com/android/a0/a054685c75c309c2b6dfd3c96972dded_screeshots_3.jpeg
comments: true
---
<i>{{ page.excerpt }}</i>
<hr />

{% include _toc.html %}

This post is about converting existing HTML into markdown text in a file like README.md.

I wrote this because I haven't seen an approach like this described.

I'm having to convert hundreds of pages I've written in HTML since the 90's.

## Orderd lists

My favorite feature of Markdown is it **automatically numbers ordered lists**!

So you can begin all items of unordered lists with a 0. 

{% highlight html %}
1. First item.
0. Second item.
9. Third item.
{% endhighlight %}

The coding above Markdown renders correctly as 1,2,3.

PROTIP: Begin the first item of an ordered list with 1, just in case. 

To make Markdown interpret a paragraph starting with a number as a list,
put a left-slash in front of the dot, as in:

{% highlight html %}
1492\. That was the year
{% endhighlight %}

## Tables in HTML

HTML tables renders well from within Markdown text document.

However, some HTML tables were used in the early days of the internet
were used to format an entire page. Such coding would need surgery to look well
since tables are now intended to fit into a text column.

## Bold and italics

CAUTION: Markdown coding are not processed within HTML tables.

So within tables continue to bold with

{% highlight html %}
<strong>emphasized</strong> rather than Markdown __emphasized__ or **emphasized**
{% endhighlight %}

which renders as:

<strong>emphasized</strong> rather than Markdown __emphasized__ or **emphasized**

Continue to italicize with:

{% highlight html %}
<em>italicized</em> rather than Markdown _italicized_ or *italicized*
{% endhighlight %}

which renders as:

<em>italicized</em> rather than Markdown _italicized_ or *italicized*


## Tools?

To see your markdown turn into HTML, use this online tool: 

   * <a target="_blank" href="http://daringfireball.net/projects/markdown/dingus">Dingus</a>

The easiest way to convert HTML to Markdown text is to use Aaron Swartz’s 

   * <a target="_blank" href="http://www.aaronsw.com/2002/html2text/">html2text.py Python script or on-line</a>
   But it has not been updated since 2011.

> My experience is that we'll need to pretty much go through each line 
to make it look good in Markdown text.

## Links

PROTIP: Keep coding HTML to link to external sites and images.

Example of HTML:

{% highlight html %}
<a taget="_blank" title="hello" href="http://wilsonmar.github.io/">my site</a>
{% endhighlight %}

> The biggest hassle with converting to Markdown text from HTML coding is that
Markdown reverses the order of text and links. 

{% highlight html %}
 [mysite](http://wilsonmar.github.io/)
{% endhighlight %}

The same goest for the alternate "automatic" format Markdown offers to link: 

{% highlight html %}
<http://wilsonmar.github.io>
{% endhighlight %}

> I'm reluctant to put external links in Markdown because
they open in the **same window**, causing my site to lose visitors to that site.

{% highlight html %}
![mysite logo](http://wilsonmar.github.io/favicon.png/ "optional title")
{% endhighlight %}

   Notice that links to images would have an exclaimation point in front.

> Markdown currently has no syntax for specifying the dimensions of an image.

To embed a YouTube video, use an HTML iframe.

{% highlight html %}
<iframe width="560" height="315" src="https://www.youtube.com/embed/Onv9nhPIBp0" frameborder="0" allowfullscreen> </iframe>
{% endhighlight %}

To specify starting the video at a specific time (1 minute 2 seconds), use a link such as:

{% highlight html %}
<a target="_blank" href="https://www.youtube.com/watch?v=Onv9nhPIBp0&t=1m2s">Link to YouTube</a>.
{% endhighlight %}

## Special characters

PROTIP: If a URL contains attributes, **convert &amp; (ampersand)**

Another aspect where it would be helpful to use tools is conversion of some special characters
that Markdown converts into escape entities that begin with an **&amp;** (ampersand),

   * **&lt;** (less than) is turned into &amp;lt;

   * **&gt;** (greater than) is turned into &amp;gt; because that's used to signify block quotes in Markdown.

   * the ampersand itself turns to &amp;amp;, as in link URLs.

Markdown treats these characters as ordinary text if there is backslash escape character in front of them:

* \\\   backslash itself
* \\`   backtick
* \\*   asterisk
* \\_   underscore
* \\{ \\}  curly braces
* \\[ \\]  square brackets
* \\( \\)  parentheses
* \\#   hash mark
* \\+   plus sign
* \\-   minus sign (hyphen)
* \\.   dot
* \\!   exclamation mark

## Horizontal rule

A line going across the page in HTML is:

{% highlight html %}
<hr />
{% endhighlight %}


## Blockquotes in HTML

Markdown ignores the HTML `<blockquote>` tag. So this appear as if it was not surrounded by the tag:

{% highlight html %}
<block>
This is a block quote.
</block>
{% endhighlight %}

## Different Parsers

The trouble with Markdown code is that different parsers render them differently into HTML.

In March, 2016 GitHub switched to the **Kramdown** parser which
claims to incorporate the capabilities of other parsers:

   * <a target="_blank" href="https://github.com/vmg/redcarpet">RedCarpet</a>

   * <a target="_blank" href="http://pandoc.org/">Pandoc</a>

   * <a target="_blank" href="http://dafoster.net/projects/rdiscount/">Rdiscount</a>


## Line breaks

Both styles of line break tags result in a new line (without a blank line in between): 
the XHTML style:

{% highlight html %}
Hello<br />there
{% endhighlight %}

or HTML-style tags:

{% highlight html %}
Hello<br>there
{% endhighlight %}


## Paragraphs

They say Markdown text is easier to write than HTML.

   * No need for `<p>` to force a blank line. Just a blank line will do.

    But avoid doing a mass change of `<p>` 

## Unordered Lists

CAUTION: Even though HTML can be written or pasted into markdown (.md) files,
HTML must be more correct than HTML read by internet browsers.

   * There must be a blank line before `<ul>` or `<ol>`.

   * For every `<li>` there needs to be a `</li>` or the rendering goes wacky.

   * There must be a blank line after anchor tags `<a name=...` and a heading text line.

PROTIP: Markdown recognizes different characters to parse into lists:

   * Asterisk

   + plus sign

   - minus sign

## Headings

Instead of the opening `<h2>` and such tags, replace with `##`
(called <a target="_blank" href="http://www.aaronsw.com/2002/atx/">Atx-style</a> headers).

Markdown recognizes up to 6 hash characters for 6 levels.

The ending '##' character is optional. It can be any number of characters.
## Tables

Alternately, <a target="_blank" href="http://docutils.sourceforge.net/mirror/setext.html">Setext-style</a> 
headers are specified (“underlined”) by a series of 
equal signs (for first-level headers) and dashes (for second-level headers):

<pre><code>
First-level H1 headers
=============

Second-level H2 headers
-------------
</code></pre>

## Liquid Markdown Syntax

Additionally, Markdown in  GitHub recognizes Liquid syntax as defined in:

   * [https://docs.shopify.com/themes/liquid/basics](https://docs.shopify.com/themes/liquid/basics)

This coding would process html as such:

<pre><code>
&#123;% highlight html %}
<strong>Hello</strong>
&#123;% endhighlight %}
</code></pre>

## Footnote

This incorporates the thorough detail about markdown coding at:

* <a target="_blank" href="http://daringfireball.net/projects/markdown/">daringfireball.net</a>                                                                       


A discussion forum about markdown is at:

* <a target="_blank" href="https://pairlist6.pair.net/mailman/listinfo/markdown-discuss/">
   pairlist6.pair.net/mailman/listinfo/markdown-discuss</a>
