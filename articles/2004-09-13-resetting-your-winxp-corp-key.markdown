--- 
wordpress_id: 14
layout: post
title: Resetting your WinXP Corp key
disqus_url: http://blog.sideline.ca/2004/09/13/resetting-your-winxp-corp-key/

<p>So I don't lose this...</p>
<p><font face="Arial" size="2"><b>Backup your Registry/System State</b></font></p>
<ul>
<li><font face="Arial" size="2">Backup your system state by clicking <b>Start </b>&amp;gt; <b>Run</b> &amp;gt; and typing <b>ntbackup &amp;gt; </b>Click the <b>Advanced Mode</b> button in the Backup Utility Wizard. &amp;gt;Click the <b>Backup</b> tab, then in <b>Click to select the check box for any drive, folder, or file that you want to back up</b>, select the <b>System State.</b></font> 
</li><li><font face="Arial" size="2">As an alternative, you can backup just the Registry by clicking <b>Start</b> &amp;gt; <b>Run</b> &amp;gt; and type in <b>Regedit</b> From within the Regedit screen, right click <b>My Computer</b>, choose <b>Export</b>, name the file whatever you choose, and click <b>Save</b></font> </li></ul>
<p><font face="Arial" size="2"><b>To change the product ID</b></font></p>
<ul>
<li><font face="Arial" size="2">Log in as the local Administrator</font> 
</li><li><font face="Arial" size="2">Click <b>Start</b> &amp;gt; <b>Run</b> &amp;gt; and type in <b>Regedit</b></font> 
</li><li><font face="Arial" size="2">Browse to HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\wpaevents</font> </li>
<li><font face="Arial" size="2">In the right pane, right-click <strong>OOBETimer</strong>, and then click <strong>Modify</strong></font> 
</li><li><font face="Arial" size="2">Change at least one digit of this value to deactivate Windows</font> 
</li><li><font face="Arial" size="2">Click <b>OK</b> and </font><font face="Arial" size="2">close <b>regedit</b></font> 
</li><li><font face="Arial" size="2">Click <b>Start </b>&amp;gt; <b>Run </b>and type in: "<b>%systemroot%\system32\oobe\msoobe.exe /a</b>"</font> 
</li><li><font face="Arial" size="2">Click <strong>Yes, I want to telephone a customer service representative to activate Windows</strong>, and then click <strong>Next</strong></font> 
</li><li><font face="Arial" size="2">Click <b>Change Product Key</b> (at the bottom)</font> 
</li><li><font face="Arial" size="2">Enter your valid Corporate Product Key</font> 
</li><li><font face="Arial" size="2">Press <b>Update</b> and close the window.</font> 
</li><li><font face="Arial" size="2">If you are returned to the previous window, click <strong>Remind me later</strong></font> 
</li><li><font face="Arial" size="2">Restart your computer</font> </li></ul>
<p><font face="Arial" size="2"><b>Verify the change</b></font></p>
<ul>
<li><font face="Arial" size="2">After the workstation restarts, click <b>Start</b> &amp;gt; <b>Run</b></font> 
</li><li><font face="Arial" size="2">Type in: "<b>%systemroot%\system32\oobe\msoobe.exe /a</b>" without the quotes.</font> 
</li><li><font face="Arial" size="2">Make sure the dialog box says '<b>your copy of windows is already activated</b>'</font> </li></ul>
