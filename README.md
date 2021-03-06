﻿<div align="center">

## Dynamic Domain Hosting


</div>

### Description

Shows how you can host multiple domains under one IP address by mapping domain names to sites within a database.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Lewis E\. Moten III](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/lewis-e-moten-iii.md)
**Level**          |Beginner
**User Rating**    |4.8 (24 globes from 5 users)
**Compatibility**  |ASP\.NET
**Category**       |[Server Side](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/server-side__10-31.md)
**World**          |[\.Net \(C\#, VB\.net\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/net-c-vb-net.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/lewis-e-moten-iii-dynamic-domain-hosting__10-1089/archive/master.zip)





### Source Code

<DIV class=Section1>
<P class=MsoNormal style="TEXT-ALIGN: center" align=center><B>Dynamic Domain Hosting</B></P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>I have a fairly large project that I’m working on within my spare time to host my own site, and sites for friends.&nbsp; I have decided to update to .Net and look at the technology that I can take advantage of.</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>My biggest beef with my current system is that I spend a lot of time setting up new websites.&nbsp; I would need to add a new website and modify its host header, paste new code in a separate folder, and change settings in the files, etc.&nbsp; My goal is to cut out the middle man … and that would be me.</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>The idea would be to update my database so that all sites would access the same database catalog.&nbsp; When a user accessed any of the domains, it would hit the same code, but look for the data associated with the host provided in the URL.</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal><B>Database</B></P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>For the task at hand, I created two tables in my database.</P>
<P class=MsoNormal>&nbsp;</P>
<TABLE class=MsoTableGrid style="BORDER-RIGHT: medium none; BORDER-TOP: medium none; BORDER-LEFT: medium none; BORDER-BOTTOM: medium none; BORDER-COLLAPSE: collapse" cellSpacing=0 cellPadding=0 border=1>
<TBODY>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: windowtext 1pt solid; PADDING-LEFT: 5.4pt; BACKGROUND: black; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 365.4pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=487 colSpan=3>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Sites</SPAN></P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 149.4pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=199>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">SiteID</SPAN></P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 87.5pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=117>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Guid</SPAN></P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 128.5pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=171>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Not null, PKey</SPAN></P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 149.4pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=199>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Description</SPAN></P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 87.5pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=117>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Varchar(255)</SPAN></P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 128.5pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=171>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Null</SPAN></P></TD></TR></TBODY></TABLE>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt"></SPAN>&nbsp;</P>
<TABLE class=MsoTableGrid style="BORDER-RIGHT: medium none; BORDER-TOP: medium none; BORDER-LEFT: medium none; BORDER-BOTTOM: medium none; BORDER-COLLAPSE: collapse" cellSpacing=0 cellPadding=0 border=1>
<TBODY>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: windowtext 1pt solid; PADDING-LEFT: 5.4pt; BACKGROUND: black; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 365.4pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=487 colSpan=3>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Domains</SPAN></P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 2.05in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=197>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">DomainID</SPAN></P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 91.8pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=122>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Guid</SPAN></P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 1.75in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=168>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Not null, PKey</SPAN></P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 2.05in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=197>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">DomainName</SPAN></P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 91.8pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=122>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Varchar(50)</SPAN></P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 1.75in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=168>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Not null, indexed</SPAN></P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 2.05in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=197>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">SiteID</SPAN></P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 91.8pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=122>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Guid</SPAN></P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 1.75in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=168>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt">Not null, FKey Sites.SiteID</SPAN></P></TD></TR></TBODY></TABLE>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>This setup allows me to assign multiple domains to the same site.&nbsp; For example, my domains may consist of http://www.lewismoten.com and http://lewismoten.com .</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal><B>ASP.Net</B></P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>My next goal was to lookup the SiteID of the domain on a page request.&nbsp; Rather then hit the database each time, I save the SiteID in a cookie on the first request.</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'"></SPAN>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'">Public</SPAN><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'"> SiteID <SPAN style="COLOR: blue">As</SPAN> System.Guid</SPAN></P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'">Private</SPAN><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'"> <SPAN style="COLOR: blue">Sub</SPAN> Page_Load …</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'">If</SPAN><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'"> Request.Cookies(<SPAN style="COLOR: red">"SiteID"</SPAN>) <SPAN style="COLOR: blue">Is</SPAN> <SPAN style="COLOR: blue">Nothing</SPAN> <SPAN style="COLOR: blue">Then</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; LoadSiteID()</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'">Else</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">Try</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SiteID = <SPAN style="COLOR: blue">New</SPAN> System.Guid(Request.Cookies(<SPAN style="COLOR: red">"SiteID"</SPAN>).Value)</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">Catch</SPAN> ex <SPAN style="COLOR: blue">As</SPAN> Exception</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: green">' problems loading cookie ... bad format?</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; LoadSiteID()</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">End</SPAN> <SPAN style="COLOR: blue">Try</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'">End</SPAN><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'"> <SPAN style="COLOR: blue">If</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: black; FONT-FAMILY: 'Courier New'">Response.Write SiteID.toString()</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'">End</SPAN><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'"> <SPAN style="COLOR: blue">Sub</SPAN></SPAN></P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>The code to load the sites identification appears like so …</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'">Private</SPAN><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'"> <SPAN style="COLOR: blue">Sub</SPAN> LoadSiteID()</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'"></SPAN>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">Dim</SPAN> Domain <SPAN style="COLOR: blue">As</SPAN> <SPAN style="COLOR: blue">String</SPAN> = Request.Url.Host</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">Dim</SPAN> oConnection <SPAN style="COLOR: blue">As</SPAN> <SPAN style="COLOR: blue">New</SPAN> SqlClient.SqlConnection()</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">Dim</SPAN> oCommand <SPAN style="COLOR: blue">As</SPAN> <SPAN style="COLOR: blue">New</SPAN> SqlClient.SqlCommand()</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">Dim</SPAN> oDataTable <SPAN style="COLOR: blue">As</SPAN> <SPAN style="COLOR: blue">New</SPAN> DataTable(<SPAN style="COLOR: red">"Sites"</SPAN>)</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">Dim</SPAN> oDataAdapter <SPAN style="COLOR: blue">As</SPAN> <SPAN style="COLOR: blue">New</SPAN> SqlClient.SqlDataAdapter()</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">Dim</SPAN> SQL <SPAN style="COLOR: blue">As</SPAN> <SPAN style="COLOR: blue">String</SPAN> = <SPAN style="COLOR: red">""</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: red; FONT-FAMILY: 'Courier New'"></SPAN>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SQL &amp;= <SPAN style="COLOR: red">"SELECT SiteID FROM Domains WHERE "</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SQL &amp;= <SPAN style="COLOR: red">"Domains.DomainName = '"</SPAN> &amp; Domain &amp; <SPAN style="COLOR: red">"'"</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: red; FONT-FAMILY: 'Courier New'"></SPAN>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; oConnection.ConnectionString = <SPAN style="COLOR: red">"data source=MyServer;initial catalog=MyDatabase;UID=MyUsername;PWD=MyPassword"</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: red; FONT-FAMILY: 'Courier New'"></SPAN>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; oCommand = <SPAN style="COLOR: blue">New</SPAN> SqlClient.SqlCommand(SQL, oConnection)</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'"></SPAN>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; oDataAdapter = <SPAN style="COLOR: blue">New</SPAN> SqlClient.SqlDataAdapter(oCommand)</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; oDataAdapter.Fill(oDataTable)</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">If</SPAN> oDataTable.Rows.Count() = <B><SPAN style="COLOR: blue">0</SPAN></B> <SPAN style="COLOR: blue">Then</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SiteID = System.Guid.Empty</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">Else</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; SiteID = <SPAN style="COLOR: blue">CType</SPAN>(oDataTable.Rows(<B><SPAN style="COLOR: blue">0</SPAN></B>).Item(<B><SPAN style="COLOR: blue">0</SPAN></B>), System.Guid)</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">End</SPAN> <SPAN style="COLOR: blue">If</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'"></SPAN>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: green">' If site could not be found within database ...</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">If</SPAN> SiteID.CompareTo(System.Guid.Empty) = <B><SPAN style="COLOR: blue">0</SPAN></B> <SPAN style="COLOR: blue">Then</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'"></SPAN>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: green">' Perhaps goto page for setting up new domains</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Response.Write(<SPAN style="COLOR: red">"Domain has not been mapped.”</SPAN><SPAN style="COLOR: black">)</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: black; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Response.End</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'"></SPAN>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">Else</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'"></SPAN>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: green">' Save SiteID in cookie</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Response.Cookies(<SPAN style="COLOR: red">"SiteID"</SPAN>).Value = SiteID.ToString</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Response.Cookies(<SPAN style="COLOR: red">"SiteID"</SPAN>).Expires = DateAdd(DateInterval.Year, <B><SPAN style="COLOR: blue">5</SPAN></B>, Now())</SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Response.Cookies(<SPAN style="COLOR: red">"SiteID"</SPAN>).Path = <SPAN style="COLOR: red">"/"</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: red; FONT-FAMILY: 'Courier New'"></SPAN>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <SPAN style="COLOR: blue">End</SPAN> <SPAN style="COLOR: blue">If</SPAN></SPAN></P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'"></SPAN>&nbsp;</P>
<P class=MsoNormal><SPAN style="FONT-SIZE: 10pt; COLOR: blue; FONT-FAMILY: 'Courier New'">End</SPAN><SPAN style="FONT-SIZE: 10pt; FONT-FAMILY: 'Courier New'"> <SPAN style="COLOR: blue">Sub</SPAN></SPAN></P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>From here you can see how I tell the user if the domain doesn’t exist within the database.&nbsp; It is possible to expand this code so that the user is sent to a setup page so that they can add there domain and/or site to the database.</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal><B>Testing</B></P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>To test the code on your local computer, you may need to modify your hosts file.&nbsp; Under Windows NT/2000/XP, you may find this file under your Windows folder by following the path to “System32\Drivers\etc\hosts”.&nbsp; The Hosts file does not have a file extension.&nbsp; If you click on it, you will be prompted to select a program to open the file.&nbsp; Scroll down the list until you locate a text editor such as notepad.</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>You will see comments within the file instructing you how to setup mappings of IP Addresses to Host Names.&nbsp; The format is to write out your IP Address followed by a space and then the name of the host you wish to map.&nbsp; For your local machine, you can use the IP Address of 127.0.0.1.&nbsp; You may already see an entry written for localhost.</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>For my test, I mapped the following domains:</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>127.0.0.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; localhost</P>
<P class=MsoNormal>127.0.0.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; www.lewismoten.com</P>
<P class=MsoNormal>127.0.0.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; lewismoten.com</P>
<P class=MsoNormal>127.0.0.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; www.alienencyclopedia.com</P>
<P class=MsoNormal>127.0.0.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; alienencyclopedia.com</P>
<P class=MsoNormal>127.0.0.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 21stCenturyJokes.com</P>
<P class=MsoNormal>127.0.0.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; www.21stCenturyJokes.com</P>
<P class=MsoNormal>127.0.0.1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; www.dummydomain.com</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>For this test, you will also need to enter these domains into your database.&nbsp; First, I created three sites:</P>
<P class=MsoNormal>&nbsp;</P>
<TABLE class=MsoTableGrid style="BORDER-RIGHT: medium none; BORDER-TOP: medium none; BORDER-LEFT: medium none; BORDER-BOTTOM: medium none; BORDER-COLLAPSE: collapse" cellSpacing=0 cellPadding=0 border=1>
<TBODY>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: windowtext 1pt solid; PADDING-LEFT: 5.4pt; BACKGROUND: black; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 5.95in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=571 colSpan=2>
<P class=MsoNormal>Sites</P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; BACKGROUND: #a6a6a6; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 2.05in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=197>
<P class=MsoNormal>SiteID</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; BACKGROUND: #a6a6a6; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 3.9in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=374>
<P class=MsoNormal>Description</P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 2.05in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=197>
<P class=MsoNormal>{F270E952-9DA7-46BC-A1BC-9F6171C58729}</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 3.9in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=374>
<P class=MsoNormal>Lewies personal website.</P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 2.05in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=197>
<P class=MsoNormal>{957DC77D-F02B-4EF0-82C1-C94E251D2FB5}</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 3.9in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=374>
<P class=MsoNormal>Everything you ever wanted to know about Aliens, but were afraid to ask.</P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 2.05in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=197>
<P class=MsoNormal>{DCFACD7A-3BBD-45A2-A89C-EF552FA952D7}</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 3.9in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=374>
<P class=MsoNormal>Jokes and Riddles for the 21<SUP>st</SUP> century.</P></TD></TR></TBODY></TABLE>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>Next, I created the domains to map to the sites:</P>
<TABLE class=MsoTableGrid style="BORDER-RIGHT: medium none; BORDER-TOP: medium none; BORDER-LEFT: medium none; BORDER-BOTTOM: medium none; BORDER-COLLAPSE: collapse" cellSpacing=0 cellPadding=0 border=1>
<TBODY>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: windowtext 1pt solid; PADDING-LEFT: 5.4pt; BACKGROUND: black; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 6.15in; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=590 colSpan=3>
<P class=MsoNormal>Domains</P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; BACKGROUND: #a6a6a6; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>DomainID</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; BACKGROUND: #a6a6a6; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 150.1pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=200>
<P class=MsoNormal>DomainName</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; BACKGROUND: #a6a6a6; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>SiteID</P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{E138132B-D516-46D7-9630-0BC09043FF87}</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 150.1pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=200>
<P class=MsoNormal>www.21stcenturyjokes.com</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{DCFACD7A-3BBD-45A2-A89C-EF552FA952D7}</P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{B1B50AD7-8F87-45AB-A9D1-79884853970E}</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 150.1pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=200>
<P class=MsoNormal>www.lewismoten.com</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{F270E952-9DA7-46BC-A1BC-9F6171C58729}</P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{5E259C7C-1404-4C53-8FD5-83074CD17043}</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 150.1pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=200>
<P class=MsoNormal>21stcenturyjokes.com</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{DCFACD7A-3BBD-45A2-A89C-EF552FA952D7}</P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{01182A96-8CBD-4CDB-80DB-90EFE4F1CE32}</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 150.1pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=200>
<P class=MsoNormal>Localhost</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{F270E952-9DA7-46BC-A1BC-9F6171C58729}</P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{A5B1548B-7265-4BF5-A103-B07065594865}</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 150.1pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=200>
<P class=MsoNormal>alienencyclopedia.com</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{957DC77D-F02B-4EF0-82C1-C94E251D2FB5}</P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{56057427-1AC8-460D-BC74-C5F21909A22A}</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 150.1pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=200>
<P class=MsoNormal>lewismoten.com</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{F270E952-9DA7-46BC-A1BC-9F6171C58729}</P></TD></TR>
<TR>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: windowtext 1pt solid; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{A0E4FACD-63F9-49EB-BB17-CC9EA7674530}</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 150.1pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=200>
<P class=MsoNormal>www.alienencyclopedia.com</P></TD>
<TD style="BORDER-RIGHT: windowtext 1pt solid; PADDING-RIGHT: 5.4pt; BORDER-TOP: medium none; PADDING-LEFT: 5.4pt; PADDING-BOTTOM: 0in; BORDER-LEFT: medium none; WIDTH: 146.35pt; PADDING-TOP: 0in; BORDER-BOTTOM: windowtext 1pt solid" vAlign=top width=195>
<P class=MsoNormal>{957DC77D-F02B-4EF0-82C1-C94E251D2FB5}</P></TD></TR></TBODY></TABLE>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>Now – we have our domains setup in the database, and the hosts file.&nbsp; Notice that I didn’t setup www.dummydomain.com.&nbsp; We will use this to test domains that do not exist within the database.</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>Compile your code and visit your web page.&nbsp; If you setup your project rite, your start up page should be the page with the code from this article.&nbsp; You should be able to press play and go from there.</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>The page will load and let you know what the GUID is for the site that the domain is mapped to.&nbsp; Try modifying the domain in your browsers address bar to the other domains in your database and see the resulting GUID change.&nbsp; Now try the dummy domain and watch as the web page tells you that the domain does not exist.</P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal><B>Outcome</B></P>
<P class=MsoNormal>&nbsp;</P>
<P class=MsoNormal>Now that you have the SiteID in your cookie, you can use this to query data from your deatabase accordingly.&nbsp; For starters, try to load the site description associated with the SiteID.</P></DIV>

