---
layout: post
title:  "Link images and markup areas semantically better"
date:   2016-03-21 16:11:49 +0100
tag: shorttipps
description: Linking content areas with semantically clean markup using css. 
---
Well this is pretty basic but in my eyes still worth noticing: so let's assume you want to set a link on whatever content consisting out of more than just plain text.  
What you probably did was to wrap your &lt;a&gt; &lt;/a&gt; tag all around the markup you wanted to link. 

###And what's even bad about it? 

The main point is that you're not able to set a proper anchor text on your link, which is a bad decision when it comes to accessibility and searchability of your content.


###So here's another way to solve it:


Example Markup:


<pre class=" language-markup">
    <code>
        &lt;div class="linked-area"&gt;
          &lt;h1&gt;Lorem Ipsum&lt;/h1&gt;
          &lt;p&gt;dolor sit amet&lt;/p&gt;
          &lt;img src="http://placehold.it/200"&gt;
          &lt;a href="http://google.com">example anchor text&lt;/a&gt;
        &lt;/div&gt;
    </code>
</pre> 
As you can see it's just a regular link including an anchor text, the only thing clickable so far is the &lt;a&gt; tag. 

Let's change this using css:

<pre class="language-css">
  <code>
  .linked-area {
    position: relative;
  }

  .linked-area a {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;

    //hiding text
    text-indent: -999999px;
    overflow: hidden;
    text-align: left;
  }
  </code>
</pre>

   
 You need to position your container &lt;div&gt; relative to limit your absolute positioned &lt;a&gt; tag within it's boundaries.  <br />
 That being sad: you have to stretch your &lt;a&gt; tag to the full size of it's containing element by giving the top, bottom, left and right attributes a value of 0. <br/>The anchor text is hidden via text-indent and overflow: hidden, if you are using compass you can just use the hide-text mixin, and that's it.   
 Now the whole &lt;div&gt; is a clickable link.  
 And the result will look like this:

 <div class="linked-area">
 <p>Lorem Ipsum</p>
 <a href="http://jannikmueller.com">this is an example link</a>
 <img src="http://placehold.it/150" />
 </div>  
 <br />  
 Want to play around with it? I made you a <a href="http://codepen.io/jnnkm/pen/vGxxqJ">codepen</a>.

 Have fun linking your areas. 