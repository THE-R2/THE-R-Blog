---
ID: 1758
post_title: >
  Visual Studio 2015 용 R 도구 1.0
  발표
author: The-R
post_date: 2017-03-24 13:01:34
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/03/24/visual-studio-2015-%ec%9a%a9-r-%eb%8f%84%ea%b5%ac-1-0-%eb%b0%9c%ed%91%9c/'
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "0"
sbg_selected_sidebar:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_replacement:
  - 'a:1:{i:0;s:0:"";}'
sbg_selected_sidebar_2:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_2_replacement:
  - 'a:1:{i:0;s:0:"";}'
slide_template:
  - default
---
I’m delighted to announce the general availability of <a href="http://microsoft.github.io/RTVS-docs/" target="_blank" rel="nofollow">R Tools 1.0 for Visual Studio 2015 (RTVS)</a>. This release will be shortly followed by R Tools 1.0 for Visual Studio 2017 in early May.

RTVS is a free and open source plug-in that turns Visual Studio into a powerful and productive R development environment. Check out <a href="https://www.youtube.com/watch?v=RcSDEfMgUvU" target="_blank" rel="nofollow">this video</a> for a quick tour of its core features:
<p class="asset-video"><iframe src="https://www.youtube.com/embed/RcSDEfMgUvU" width="450" height="281" frameborder="0" allowfullscreen="allowfullscreen" data-mce-fragment="1"></iframe></p>

<h2>Core IDE Features</h2>
RTVS builds on Visual Studio, which means you get numerous features for free: from using multiple languages to word-class Editing and Debugging to over 7,000 extensions for every need:
<ul>
 	<li><a href="http://microsoft.github.io/RTVS-docs/polyglot.html" target="_blank" rel="nofollow">A polyglot IDE</a> – VS supports R, Python, C++, C#, Node.js, SQL, etc. projects simultaneously.</li>
 	<li><a href="http://microsoft.github.io/RTVS-docs/editing.html" target="_blank" rel="nofollow">Editor</a> – complete editing experience for R scripts and functions, including detachable/tabbed windows, syntax highlighting, and much more.</li>
 	<li><a href="http://microsoft.github.io/RTVS-docs/intellisense.html" target="_blank" rel="nofollow">IntelliSense</a> – (aka auto-completion) available in both the editor and the Interactive R window.</li>
 	<li><a href="http://microsoft.github.io/RTVS-docs/interactive-repl.html" target="_blank" rel="nofollow">R Interactive Window</a> – work with the R console directly from within Visual Studio.</li>
 	<li><a href="http://microsoft.github.io/RTVS-docs/history.html" target="_blank" rel="nofollow">History window</a> – view, search, select previous commands and send to the Interactive window.</li>
 	<li><a href="http://microsoft.github.io/RTVS-docs/variable-explorer.html" target="_blank" rel="nofollow">Variable Explorer</a> – drill into your R data structures and examine their values.</li>
 	<li><a href="http://microsoft.github.io/RTVS-docs/plotting.html" target="_blank" rel="nofollow">Plotting</a> – see all of your R plots in a Visual Studio tool window.</li>
 	<li><a href="http://microsoft.github.io/RTVS-docs/debugging.html" target="_blank" rel="nofollow">Debugging</a> – breakpoints, stepping, watch windows, call stacks and more.</li>
 	<li><a href="http://microsoft.github.io/RTVS-docs/rmarkdown.html" target="_blank" rel="nofollow">R Markdown</a> – R Markdown/knitr support with export to Word and HTML.</li>
 	<li><a href="http://microsoft.github.io/RTVS-docs/git.html" target="_blank" rel="nofollow">Git</a> – source code control via Git and GitHub.</li>
 	<li><a href="http://microsoft.github.io/RTVS-docs/extensions.html" target="_blank" rel="nofollow">Extensions</a> – over 7,000 Extensions covering a wide spectrum from Data to Languages to Productivity.</li>
 	<li><a href="http://microsoft.github.io/RTVS-docs/help.html" target="_blank" rel="nofollow">Help</a> – use ? and ?? to view R documentation within Visual Studio.</li>
</ul>
<a class="asset-img-link" href="http://revolution-computing.typepad.com/.a/6a010534b1db25970b01bb0986bf01970d-pi" target="_blank" rel="nofollow"><img class="asset asset-image at-xid-6a010534b1db25970b01bb0986bf01970d image-full img-responsive" title="RTVS1" src="http://revolution-computing.typepad.com/.a/6a010534b1db25970b01bb0986bf01970d-800wi" alt="RTVS1" border="0" data-lazy-loaded="true" /></a>
<h2>It’s Enterprise-Grade</h2>
RTVS includes various features that address the needs of individual as well as Data Science teams, for example:
<h3>SQL Server 2016</h3>
RTVS integrates with <a href="https://msdn.microsoft.com/en-us/library/mt604845.aspx" target="_blank" rel="nofollow">SQL Server 2016 R Services</a> and <a href="https://msdn.microsoft.com/en-us/mt186501.aspx" target="_blank" rel="nofollow">SQL Server Tools for Visual Studio 2015</a>. These separate downloads enhance RTVS with support for syntax coloring and Intellisense, <a href="http://microsoft.github.io/RTVS-docs/sqlserver.html" target="_blank" rel="nofollow">interactive queries</a>, and deployment of <a href="http://microsoft.github.io/RTVS-docs/sqlserver.html" target="_blank" rel="nofollow">stored procedures</a> directly from Visual Studio.

<a class="asset-img-link" href="http://revolution-computing.typepad.com/.a/6a010534b1db25970b01bb0986bf14970d-pi" target="_blank" rel="nofollow"><img class="asset asset-image at-xid-6a010534b1db25970b01bb0986bf14970d image-full img-responsive" title="RTVS2" src="http://revolution-computing.typepad.com/.a/6a010534b1db25970b01bb0986bf14970d-800wi" alt="RTVS2" border="0" data-lazy-loaded="true" /></a>
<h3>Microsoft R Client</h3>
Use the stock CRAN R interpreter, or the enhanced Microsoft R Client and its <a href="https://msdn.microsoft.com/en-us/microsoft-r/scaler-getting-started" target="_blank" rel="nofollow">ScaleR</a> functions that support multi-core and cluster computing for practicing data science at scale.
<h3>Visual Studio Team Services</h3>
Integrated support for git, continuous integration, agile tools, release management, testing, reporting, bug and work-item tracking through <a href="https://www.visualstudio.com/vso/" target="_blank" rel="nofollow">Visual Studio Team Services</a>. Use our hosted service or host it yourself privately.
<h3>Remoting</h3>
Whether it’s data governance, security, or running large jobs on a powerful server, RTVS <a href="http://microsoft.github.io/RTVS-docs/remote-execution.html" target="_blank" rel="nofollow">workspaces</a> enable setting up your own R server or connecting to one in the cloud.
<h2>The road ahead</h2>
We’re very excited to officially bring another language to the Visual Studio family!  Along with <a href="https://www.visualstudio.com/vs/python/" target="_blank" rel="nofollow">Python Tools for Visual Studio</a>, you have the two main languages for tackling most any analytics and ML related challenge.  In the near future (~May), we’ll release RTVS for Visual Studio 2017 as well. We’ll also resurrect the “Data Science workload” in VS2017 which gives you R, Python, F# and all their respective package distros in one convenient install. Beyond that, we’re looking forward to hearing from you on what features we should focus on next! R package development? Mixed R+C debugging? Model deployment? VS Code/R for cross-platform development? Let us know at the <a href="https://github.com/Microsoft/RTVS" target="_blank" rel="nofollow">RTVS Github repository</a>!

Thank you!

<strong>Bits</strong>: <a href="http://microsoft.github.io/RTVS-docs/installation" target="_blank" rel="nofollow">http://microsoft.github.io/RTVS-docs/installation
</a><strong>Code</strong>: <a href="https://github.com/Microsoft/RTVS" target="_blank" rel="nofollow">https://github.com/Microsoft/RTVS
</a><strong>Docs</strong>: <a href="http://microsoft.github.io/RTVS-docs" target="_blank" rel="nofollow">http://microsoft.github.io/RTVS-docs</a>

소스: <em><a href="https://www.r-bloggers.com/announcing-r-tools-1-0-for-visual-studio-2015/">Announcing R Tools 1.0 for Visual Studio 2015 | R-bloggers</a></em>