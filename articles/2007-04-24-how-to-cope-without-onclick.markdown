--- 
wordpress_id: 310
layout: post
title: How to cope without onClick
disqus_url: http://blog.sideline.ca/2007/04/24/how-to-cope-without-onclick/

<p>I recently came across <a href="http://myersds.com/notebook/2006/09/10/multiple_submit_buttons_on_a_form_with_rails">a short article</a> that described how to handle multiple submit buttons in one form with Rails.  For example, if you were writing code for a blogging application, you might want to have a button to <em>Save and Publish</em> and another button to <em>Save as Draft</em>.  Both of these buttons work on the same form contents but would spawn different actions.  You can read about the solution at "<a href="http://myersds.com/notebook/2006/09/10/multiple_submit_buttons_on_a_form_with_rails">How To Use Multiple Submit Buttons on a Form with Rails</a>."</p>

<p>Reading this article reminded me how long it's been since I've had to worry about this particular problem.  I definitely remember tracking down a similar solution 8 or 9 years ago when I was using ASP.  But this problem went away with the rise of ASP.Net.</p>

<p>ASP.Net blurred the line between a web app and a desktop app.  In ASP.Net, the need to work directly with the HTML of a form was drastically reduced.  I simply had to add an onClick handler to my button and then deal with the postback in my code-behind.</p>

<p>While I like the feeling of being closer to the HTML metal in Rails, there's something to be said for the simplicity of ASP.Net's abstraction.  What's your preference?</p>
