--- 
wordpress_id: 111
layout: post
title: DNN 2.x to 3.x conversion
disqus_url: http://blog.sideline.ca/2005/03/12/dnn-2x-to-3x-conversion/

<p>A <a href="http://asp.net/Forums/ShowPost.aspx'tabindex=1&amp;amp;PostID=800721">good post on how to convert a module from 2.x to 3.x</a>.</p>

>Depending on your modules, upgrading to 3.0 is not that difficult. To upgrade just add your module project to one of the 3.0 solutions. (Or you can create a new one but you will need to create another bulid project)
>	
>* Open up the <a title="" href="http://www.dotnetnuke.com">DotNetNuke</a> Visual Studio.NET solution file (C:\DotNetNuke\Solutions\DotNetNuke.DesktopModules\DotNetNuke.DesktopModules.sln) 
>* In the Solution Explorer right-click on the <a title="" href="http://www.dotnetnuke.com">DotNetNuke</a> Solution (not the project) and select Add | Existing project 
>* Navigate to your project and click ok to add it to the soultion. 
>* Next change where your module builds so that it builds into its OWN bin directory 
>
>To allow the BuildSupport project to add our dll to the <a title="" href="http://www.dotnetnuke.com">DotNetNuke</a> project, you need to add a reference to your project in the BuildSupport project. 
>
>* Right-click on the reference folder located below the BuildSupport project select Add Reference. 
>* Select the Projects tab. 
>* Double-click on your project to place it in the Selected Components box. 
>* Click OK to add the reference. 
>
>Once this is done build your project and go through the errors that arise. These will be becuase of the Namespace reorginization. Just look at the class it is having trouble finding, do a search in the code to find what namespace it now resides in and fix the references. 
>
>You will then need to decide if you will be implementing the new interfaces. You must implement IActionable to use the module context menu. But the others ISearchable, IPortable,IUpgradable are useful but not necessary for you module to work. 
>
>Many items are accessed in a different way (Like the PortalSettings) and some now hold different data(Like Context.User.Identity.Name) but depending on what you module does it should not be difficult to find its replacement. 
>
>Hope this helps to get you started. 
