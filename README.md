<div align="center">

## generating "real" random numbers


</div>

### Description

This article tells you how to generate real random numbers using rand(), srand(), and time()
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[r0m4n](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/r0m4n.md)
**Level**          |Beginner
**User Rating**    |5.0 (25 globes from 5 users)
**Compatibility**  |C, C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+, UNIX C\+\+
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__3-1.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/r0m4n-generating-real-random-numbers__3-3020/archive/master.zip)





### Source Code

```
<html>
<head>
<meta http-equiv=Content-Type content="text/html; charset=windows-1252">
<meta name=ProgId content=Word.Document>
<meta name=Generator content="Microsoft Word 9">
<meta name=Originator content="Microsoft Word 9">
<link rel=File-List href="./realrand_files/filelist.xml">
<title>Generating &#8220;real&#8221; random numbers</title>
<style>
<!--
 /* Style Definitions */
p.MsoNormal, li.MsoNormal, div.MsoNormal
	{mso-style-parent:"";
	margin:0in;
	margin-bottom:.0001pt;
	mso-pagination:widow-orphan;
	font-size:12.0pt;
	font-family:"Times New Roman";
	mso-fareast-font-family:"Times New Roman";}
h1
	{mso-style-next:Normal;
	margin:0in;
	margin-bottom:.0001pt;
	mso-pagination:widow-orphan;
	page-break-after:avoid;
	mso-outline-level:1;
	font-size:12.0pt;
	font-family:"Times New Roman";
	mso-font-kerning:0pt;
	font-weight:normal;
	font-style:italic;}
a:link, span.MsoHyperlink
	{color:blue;
	text-decoration:underline;
	text-underline:single;}
a:visited, span.MsoHyperlinkFollowed
	{color:purple;
	text-decoration:underline;
	text-underline:single;}
@page Section1
	{size:8.5in 11.0in;
	margin:1.0in 1.25in 1.0in 1.25in;
	mso-header-margin:.5in;
	mso-footer-margin:.5in;
	mso-paper-source:0;}
div.Section1
	{page:Section1;}
-->
</style>
</head>
<body lang=EN-US link=blue vlink=purple style='tab-interval:.5in'>
<div class=Section1>
<p class=MsoNormal align=center style='text-align:center'><b>Generating &#8220;real&#8221;
random numbers.<o:p></o:p></b></p>
<h1>The Problem</h1>
<p class=MsoNormal>Well as you may know rand() returns the next pseudo-random
number in the series. The default seed for the series is 1. You can change it
by calling srand().But calling srand() doesn&#8217;t always mean that you will get &#8220;real&#8221;
random numbers.For example the following code looks like it would return random
numbers but it does not:</p>
<p class=MsoNormal><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoNormal>#include &lt;stdlib.h&gt; /* header for rand() and srand()
*/</p>
<p class=MsoNormal>#include &lt;stdio.h&gt; /* io header */</p>
<p class=MsoNormal>int main()</p>
<p class=MsoNormal>{</p>
<p class=MsoNormal><span style='mso-tab-count:1'>            </span>srand(rand());</p>
<p class=MsoNormal><span style='mso-tab-count:1'>            </span>for(int
i=0;i&lt;=9;i++)</p>
<p class=MsoNormal><span style='mso-tab-count:1'>            </span><span
style='mso-tab-count:1'>            </span>printf(&#8220;%i\n&#8221;,rand());</p>
<p class=MsoNormal><span style='mso-tab-count:1'>            </span>return 0;</p>
<p class=MsoNormal>}</p>
<p class=MsoNormal><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoNormal>The output of this program will be the same each time you
run it. Feel free to test this.</p>
<p class=MsoNormal><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<h1>Solution</h1>
<p class=MsoNormal><span style="mso-spacerun: yes"> </span>As mentioned above
srand() can be used to change the seed. But if you set it to a constant the
series would still be the same. So we use srand(time(0)). time() returns a
time_t object. You can interpret it as an integer and the value will always
differ. So, now we would have:</p>
<p class=MsoNormal><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoNormal>#include &lt;stdlib.h&gt; /* header for rand() and srand()
*/</p>
<p class=MsoNormal>#include &lt;stdio.h&gt; /* io header */</p>
<p class=MsoNormal>#include &lt;time.h&gt; /* header needed for time() */</p>
<p class=MsoNormal>int main()</p>
<p class=MsoNormal>{</p>
<p class=MsoNormal><span style='mso-tab-count:1'>            </span>srand(time(0));</p>
<p class=MsoNormal><span style='mso-tab-count:1'>            </span>for(int
i=0;i&lt;=9;i++)</p>
<p class=MsoNormal><span style='mso-tab-count:1'>            </span><span
style='mso-tab-count:1'>            </span>printf(&#8220;%i\n&#8221;,rand());</p>
<p class=MsoNormal><span style='mso-tab-count:1'>            </span>return 0;</p>
<p class=MsoNormal>}</p>
<p class=MsoNormal><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<p class=MsoNormal>Now we have real random numbers.</p>
<p class=MsoNormal><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></p>
<h1>Contact</h1>
<p class=MsoNormal>If you have any questions/comments e-mail me at <a
href="mailto:r0m4n@yahoo.com?subject=RE: real random numbers">r0m4n@yahoo.com</a></p>
<p class=MsoNormal>I hope you enjoyed this tutorial, and have a nice day.</p>
</div>
</body>
</html>
```

