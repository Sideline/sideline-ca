--- 
wordpress_id: 213
layout: post
title: How to tell if I&#8217;m using OOP'
disqus_url: http://blog.sideline.ca/2005/12/01/how-to-tell-if-im-using-oop/

<p>I've come up with a quick (and incredibly shoddy) way to tell if I'm using OOP practices.  The thing that I like about it is that it's really simple.  Use it at your own risk and switch language suffixes as required.</p>
<ul>
<li>Count how many *.vb files you have in your current solution.  Assign this count to A.</li>
<li>Then count how many of those are *.ascx.vb files.  Assign this count to B.</li>
<li>Subtract B from A.</li></ul>
<p>If you end up with a value that is greater than 0, chances are that you're using OOP.  Of course, you could have some helper files that aren't OOP, but that's where the 'incredibly shoddy' part of this methodology begins to expose itself.</p>
<p>Seriously though, I am absolutely amazed at how many projects do not have any class files other than the code-behind files.  Using a code-behind is not OOP.  It is procedural programming that is disguised to look like OOP.  It is (and this may shock some of you) soooooooo VB6.</p>
<p>For those of you that I've now demoted to VB6 developers, you're in luck.  There is help available.  Learn what an interface is and why you should use it.  Learn what an abstract class and why you should use it.  Learn about polymorphism and why it is useful.  Read about design patterns.</p>
<p>Trust me ' it will make you a better person.  :-)</p>
