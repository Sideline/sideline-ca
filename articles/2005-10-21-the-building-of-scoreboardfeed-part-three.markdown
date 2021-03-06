--- 
wordpress_id: 181
layout: post
title: The Building of ScoreboardFeed, Part Three
disqus_url: http://blog.sideline.ca/2005/10/21/the-building-of-scoreboardfeed-part-three/

Now that I've discussed <a href="/blogs/mike/archive/2005/10/05/The_Building_of_ScoreboardFeed.aspx">why I wanted to build ScoreboardFeed</a> and some of the <a href="/blogs/mike/archive/2005/10/11/The_Building_of_ScoreboardFeed_Part_Two.aspx">base classes that are within it</a>, it's time to look at the nitty gritty - the parsing.<br />
<br />
The code for <a href="http://xmlsports.sourceforge.net/">XMLSports</a> contained <a href="http://proxy.espn.go.com/wireless/espn/html/pocketpc">URL's to ESPN scoreboards</a> for <a href="http://proxy.espn.go.com/nhl/wireless/html/scoreboard'dvc=1">NHL</a>, <a href="http://proxy.espn.go.com/nba/wireless/html/scoreboard'dvc=1">NBA</a>, <a href="http://proxy.espn.go.com/nfl/wireless/html/scoreboard'dvc=1">NFL</a>, <a href="http://proxy.espn.go.com/mlb/wireless/html/scoreboard'dvc=1">Major League Baseball</a>, <a href="http://proxy.espn.go.com/ncb/wireless/html/scoreboard'dvc=1">College Basketball</a> and <a href="http://proxy.espn.go.com/ncf/wireless/html/scoreboard'dvc=1">College Football</a>. 
The nice thing about these URL's was that they pointed to HTML pages
that were designed for viewing on devices like Pocket PC's.  That
means that the pages were small and didn't contain a lot of
advertisements or scripting.  To me, that means that they're
perfect for parsing since there isn't too much extra content that I
would sift through.<br />
<br />
In addtion to that, the HTML for each of the scoreboards was very
similar.  Actually, forget about similar - each scoreboard had the
exact same structure!  That meant that once I had written a class
to parse one scoreboard, I should be able to parse the rest of them
without changing anything except for the URL reference.  I'm <a href="http://blog.outer-court.com/archive/2005-08-24-n14.html">lazy and somewhat dumb</a>, so I liked this idea.<br />
<br />
At first, my procedural programmer brain thought that I could create
one class for this.  I would then build a method that could take
the different urls as a parameter.  After I thought about this for
more than a second and realized that I had to start thinking OO, I
changed my mind.  Instead, I would build a nice base class that
contained all of the logic for parsing the HTML.  Then, I would
create a series of classes for each scoreboard that inherited this base
class.  A different subclass would be created for each sport and
would contain the sport-specific information such as the URL, sport
name, etc.<br />
<br />
The beauty of this design is that it can consolidate and abstract my
code at the same time.  It consolidates my code because it allows
me to put all of my logic and processing into the base class. 
However, if ESPN decides one day that NHL scores should be represented
differently, I can still implement the specific NHL code in the NHL
class because I've abstracted this class away from all of the other
classes.<br />
<br />
Anyways, I followed the source code from <a href="http://xmlsports.sourceforge.net/">XMLSports</a>
fairly closely in my parsing routines.  They had some good ideas
for breaking out the NFL scores into multiple days (it's the only
scoreboard that does this) so I followed along.  The regular
expressions had to change a little bit, but I was able to make the
changes using <a href="http://regex.osherove.com/">The Regulator</a>:<br />


  
    
  
    <pre>Namespace Espn<br /><br />    Public MustInherit Class EspnScoreboard<br />        Inherits Scoreboard<br /><br />        Private _ScoreboardUrl As String = "http://proxy.espn.go.com/wireless/espn/html/pocketpc"
        Private _SportName As String = "Default"
        Private Const mNotes As String = "All Times Eastern"
        Private Const mPublisherName As String = "ESPN"
        Private _isMultiDayScoreboard As Boolean = False

        Protected Sub New(ByVal ScoreboardUrl As String, ByVal SportName As String)<br />            MyBase.New()<br />            _ScoreboardUrl = ScoreboardUrl<br />            _SportName = SportName<br />        End Sub

        Protected Sub New(ByVal ScoreboardRetriever As IScoreboardRetriever, ByVal ScoreboardUrl As String, ByVal SportName As String)<br />            MyBase.New(ScoreboardRetriever)<br />            _ScoreboardUrl = ScoreboardUrl<br />            _SportName = SportName<br />        End Sub
        
        .
        .
        .
        
    End Class
End Namespace
        
</pre>
  
You can view the rest of the code in the source files to see the actual
parsing.  What I really wanted to show here is that I've created a
new abstract class called EspnScoreboard.  It inherits from the
base Scoreboard class.  It has some private members and some
overloaded constructors.  The constructors are where the magic
happens.<br />
<br />
To give you a better idea where the magic is coming from, here's the code for the NHL class:<br />


  
    
  
    <pre>Namespace Espn<br /><br />    &amp;lt;ScoreboardName("ESPN - NHL")&amp;gt; _<br />    Public Class NhlScoreboard<br />        Inherits EspnScoreboard<br /><br />        Private Const mScoreboardUrl As String = "http://proxy.espn.go.com/nhl/wireless/html/scoreboard'dvc=1"
        Private Const mSportName As String = "NHL"<br />
        Public Sub New()<br />            MyBase.New(mScoreboardUrl, mSportName)<br />        End Sub

        Public Sub New(ByVal ScoreboardRetriever As IScoreboardRetriever)<br />            MyBase.New(ScoreboardRetriever, mScoreboardUrl, mSportName)<br />        End Sub
    End Class
End Namespace</pre>NhlScoreboard
inherits from EspnScoreboard, which in turn inherits from
Scoreboard.  Since  Scoreboard and EspnScoreboard are both
abstract classes, NhlScoreboard is the only one of these three classes
that can be directly instantiated.  When the class is instantiated
without any parameters (i.e. using only the UrlRetriever), it makes a call into its base class (EspnScoreboard) to call the
constructor that takes two string parameters - the ScoreboardUrl and
the SportName.  Because NhlScoreboard is relying on EspnScoreboard
to do all of the work, it only exists as a couple of constants and two
constructors.  Nice, eh'<br />
<br />
That's enough for this post.  In the next post, I'll talk about the parsing routines that are used in EspnScoreboard.<br />
<br />
<br />
<br />
