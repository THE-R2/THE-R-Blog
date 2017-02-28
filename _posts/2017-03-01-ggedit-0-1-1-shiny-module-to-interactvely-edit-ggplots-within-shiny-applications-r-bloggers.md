---
ID: 1517
post_title: 'ggedit 0.1.1: Shiny module to interactvely edit ggplots within Shiny applications | R-bloggers'
author: The-R
post_date: 2017-03-01 00:11:27
post_excerpt: ""
layout: post
permalink: >
  http://the-r.kr/2017/03/01/ggedit-0-1-1-shiny-module-to-interactvely-edit-ggplots-within-shiny-applications-r-bloggers/
published: true
inline_featured_image:
  - "0"
---
<blockquote>ggedit is a package that lets users interactively edit ggplot layer and theme aesthetics. In a previous <a href="https://www.r-bloggers.com/ggedit-interactive-ggplot-aesthetic-and-theme-editor/" target="_blank" rel="nofollow">post</a> we showed you how to use it in a collaborative workflow using standard R scripts. More importantly, we <a href="https://www.r-bloggers.com/ggedit-0-0-2-a-gui-for-advanced-editing-of-ggplot2-objects/" target="_blank" rel="nofollow">highlighted</a> that ggedit outputs to the user, after editing, updated: gg plots, layers, scales and themes as both self-contained objects <em>and</em> script that you can paste directly in your code.
<div id="installation" class="section level3">
<h3>Installation</h3>
<div>
<div id="highlighter_100007" class="syntaxhighlighter  r">
<table border="0" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td class="gutter">
<div class="line number1 index0 alt2">1</div></td>
<td class="code">
<div class="container">
<div class="line number1 index0 alt2"><code class="r plain">devtools::</code><code class="r functions">install_github</code><code class="r plain">(</code><code class="r string">'metrumresearchgroup/ggedit'</code><code class="r plain">,subdir=</code><code class="r string">'ggedit'</code><code class="r plain">)</code></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
</div>
<div id="version-0.1.1-updates" class="section level3">
<h3>version 0.1.1 Updates</h3>
<ul>
 	<li><strong>ggEdit Shiny module</strong>: use ggedit as part of any Shiny application.</li>
 	<li><strong>gggsave</strong>: generalized ggsave to write multiple outputs of ggplot to a single file and/or multiple files from a single call. Plots can be saved to various graphic devices.</li>
</ul>
</div>
<div id="ggedit-shiny-module" class="section level3">
<h3>ggEdit Shiny module</h3>
This post will demonstrate a new method to use ggedit, <a href="https://shiny.rstudio.com/articles/modules.html" target="_blank" rel="nofollow">Shiny modules</a>. A Shiny module is a chunk of Shiny code that can be reused many times in the same application, but generic enough so it can be applied in any Shiny app (in simplest terms think of it as a Shiny function). By making ggedit a Shiny module we can now replace any <a href="https://shiny.rstudio.com/reference/shiny/latest/renderPlot.html" target="_blank" rel="nofollow">renderPlot()</a> call that inputs a ggplot and outputs in the UI <a href="https://shiny.rstudio.com/reference/shiny/latest/plotOutput.html" target="_blank" rel="nofollow">plotOutput()</a>, with an interactive ggedit layout. The analogy between how to use the ggEdit module in comparison to a standard renderPlot call can be seen in the table below.
<table>
<tbody>
<tr>
<td></td>
<td>Standard Shiny</td>
<td>Shiny Module</td>
</tr>
<tr>
<td>Server</td>
<td><code>output$id=renderPlot(p)</code></td>
<td><code>reactiveOutput=callModule(ggEdit,id,reactive(p))</code></td>
</tr>
<tr>
<td>UI</td>
<td><code>plotOutput(id)</code></td>
<td><code>ggEditUI(id)</code></td>
</tr>
</tbody>
</table>
We can see that there are a few differences in the calls. To call a module you need to run a Shiny function <a href="https://shiny.rstudio.com/reference/shiny/latest/callModule.html" target="_blank" rel="nofollow">callModule</a>, in this case ggEdit. Next, a character id for the elements the module will create in the Shiny environment and finally the arguments that are expected by the module, in this case a reactive object that outputs a ggplot or list of ggplots. This is coupled with ggEditUI, which together create a ggedit environment to edit the plots during a regular Shiny app.
In addition to the output UI the user also gets a reactive output that has all the objects that are in the regular ggedit package (plots, layers, scales, themes) both in object and script forms. This has great advantages if you want to let users edit plots while keeping track of what they are changing. A realistic example of this would be clients (be it industry or academia) that are shown a set of default plots, with the appropriate data, and then they are given the opportunity to customize according to their specifications. Once they finish editing, the script is automatically saved to the server, updating the clients portfolio with their preferred aesthetics. No more email chains on changing a blue point to an aqua star!
Below is a small example of a static ggplot using renderPlot/plotOutput and how to call the same plot and a list of plots using ggEdit/ggeditUI. We added a small reactive text output so you can see the real-time changes of the aesthetic editing being returned to the server
<div class="jetpack-video-wrapper"><iframe class="youtube-player" src="https://www.youtube.com/embed/pJ1kbd_OVwg?version=3&amp;rel=1&amp;%23038;fs=1&amp;%23038;autohide=2&amp;%23038;showsearch=0&amp;%23038;showinfo=1&amp;%23038;iv_load_policy=1&amp;%23038;wmode=transparent" width="450" height="402" allowfullscreen="allowfullscreen" data-mce-fragment="1"></iframe></div>
</div>
<div id="source-code-for-example" class="section level3">
<h3>Source Code for example</h3>
<div>
<div id="highlighter_610993" class="syntaxhighlighter  r">
<table border="0" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td class="gutter">
<div class="line number1 index0 alt2">1</div>
<div class="line number2 index1 alt1">2</div>
<div class="line number3 index2 alt2">3</div>
<div class="line number4 index3 alt1">4</div>
<div class="line number5 index4 alt2">5</div>
<div class="line number6 index5 alt1">6</div>
<div class="line number7 index6 alt2">7</div>
<div class="line number8 index7 alt1">8</div>
<div class="line number9 index8 alt2">9</div>
<div class="line number10 index9 alt1">10</div>
<div class="line number11 index10 alt2">11</div>
<div class="line number12 index11 alt1">12</div>
<div class="line number13 index12 alt2">13</div>
<div class="line number14 index13 alt1">14</div>
<div class="line number15 index14 alt2">15</div>
<div class="line number16 index15 alt1">16</div>
<div class="line number17 index16 alt2">17</div>
<div class="line number18 index17 alt1">18</div>
<div class="line number19 index18 alt2">19</div>
<div class="line number20 index19 alt1">20</div>
<div class="line number21 index20 alt2">21</div>
<div class="line number22 index21 alt1">22</div>
<div class="line number23 index22 alt2">23</div>
<div class="line number24 index23 alt1">24</div>
<div class="line number25 index24 alt2">25</div>
<div class="line number26 index25 alt1">26</div>
<div class="line number27 index26 alt2">27</div>
<div class="line number28 index27 alt1">28</div>
<div class="line number29 index28 alt2">29</div>
<div class="line number30 index29 alt1">30</div>
<div class="line number31 index30 alt2">31</div>
<div class="line number32 index31 alt1">32</div>
<div class="line number33 index32 alt2">33</div>
<div class="line number34 index33 alt1">34</div>
<div class="line number35 index34 alt2">35</div></td>
<td class="code">
<div class="container">
<div class="line number1 index0 alt2"><code class="r functions">library</code><code class="r plain">(ggedit)</code></div>
<div class="line number2 index1 alt1"><code class="r plain">server = </code><code class="r keyword">function</code><code class="r plain">(input, output,session) {</code></div>
<div class="line number3 index2 alt2"><code class="r plain">p1=</code><code class="r functions">ggplot</code><code class="r plain">(iris,</code><code class="r functions">aes</code><code class="r plain">(x=Sepal.Length,y=Sepal.Width,colour=Species))+</code><code class="r functions">geom_point</code><code class="r plain">()</code></div>
<div class="line number4 index3 alt1"><code class="r plain">p2=</code><code class="r functions">ggplot</code><code class="r plain">(iris,</code><code class="r functions">aes</code><code class="r plain">(x=Sepal.Length,y=Sepal.Width,colour=Species))+</code><code class="r functions">geom_line</code><code class="r plain">()+</code><code class="r functions">geom_point</code><code class="r plain">()</code></div>
<div class="line number5 index4 alt2"><code class="r plain">p3=</code><code class="r functions">list</code><code class="r plain">(p1=p1,p2=p2)</code></div>
<div class="line number6 index5 alt1"><code class="r plain">output$p=</code><code class="r functions">renderPlot</code><code class="r plain">({p1})</code></div>
<div class="line number7 index6 alt2"></div>
<div class="line number8 index7 alt1"><code class="r plain">outp1=</code><code class="r functions">callModule</code><code class="r plain">(ggEdit,</code><code class="r string">'pOut1'</code><code class="r plain">,obj=</code><code class="r functions">reactive</code><code class="r plain">(</code><code class="r functions">list</code><code class="r plain">(p1=p1)))</code></div>
<div class="line number9 index8 alt2"><code class="r plain">outp2=</code><code class="r functions">callModule</code><code class="r plain">(ggEdit,</code><code class="r string">'pOut2'</code><code class="r plain">,obj=</code><code class="r functions">reactive</code><code class="r plain">(p3))</code></div>
<div class="line number10 index9 alt1"></div>
<div class="line number11 index10 alt2"><code class="r plain">output$x1=</code><code class="r functions">renderUI</code><code class="r plain">({</code></div>
<div class="line number12 index11 alt1"><code class="r plain">layerTxt=</code><code class="r functions">outp1</code><code class="r plain">()$UpdatedLayerCalls$p1[[1]]</code></div>
<div class="line number13 index12 alt2"><code class="r functions">aceEditor</code><code class="r plain">(outputId = </code><code class="r string">'layerAce'</code><code class="r plain">,value=layerTxt,</code></div>
<div class="line number14 index13 alt1"><code class="r plain">mode = </code><code class="r string">'r'</code><code class="r plain">, theme = </code><code class="r string">'chrome'</code><code class="r plain">,</code></div>
<div class="line number15 index14 alt2"><code class="r plain">height = </code><code class="r string">'100px'</code><code class="r plain">, fontSize = 12,wordWrap = T)</code></div>
<div class="line number16 index15 alt1"><code class="r plain">})</code></div>
<div class="line number17 index16 alt2"></div>
<div class="line number18 index17 alt1"><code class="r plain">output$x2=</code><code class="r functions">renderUI</code><code class="r plain">({</code></div>
<div class="line number19 index18 alt2"><code class="r plain">themeTxt=</code><code class="r functions">outp1</code><code class="r plain">()$UpdatedThemeCalls$p1</code></div>
<div class="line number20 index19 alt1"><code class="r functions">aceEditor</code><code class="r plain">(outputId = </code><code class="r string">'themeAce'</code><code class="r plain">,value=themeTxt,</code></div>
<div class="line number21 index20 alt2"><code class="r plain">mode = </code><code class="r string">'r'</code><code class="r plain">, theme = </code><code class="r string">'chrome'</code><code class="r plain">,</code></div>
<div class="line number22 index21 alt1"><code class="r plain">height = </code><code class="r string">'100px'</code><code class="r plain">, fontSize = 12,wordWrap = T)</code></div>
<div class="line number23 index22 alt2"><code class="r plain">})</code></div>
<div class="line number24 index23 alt1"><code class="r plain">}</code></div>
<div class="line number25 index24 alt2"></div>
<div class="line number26 index25 alt1"><code class="r plain">ui=</code><code class="r functions">fluidPage</code><code class="r plain">(</code></div>
<div class="line number27 index26 alt2"><code class="r functions">conditionalPanel</code><code class="r plain">(</code><code class="r string">"input.tbPanel=='tab2'"</code><code class="r plain">,</code></div>
<div class="line number28 index27 alt1"><code class="r functions">sidebarPanel</code><code class="r plain">(</code><code class="r functions">uiOutput</code><code class="r plain">(</code><code class="r string">'x1'</code><code class="r plain">),</code><code class="r functions">uiOutput</code><code class="r plain">(</code><code class="r string">'x2'</code><code class="r plain">))),</code></div>
<div class="line number29 index28 alt2"><code class="r functions">mainPanel</code><code class="r plain">(</code></div>
<div class="line number30 index29 alt1"><code class="r functions">tabsetPanel</code><code class="r plain">(id = </code><code class="r string">'tbPanel'</code><code class="r plain">,</code></div>
<div class="line number31 index30 alt2"><code class="r functions">tabPanel</code><code class="r plain">(</code><code class="r string">'renderPlot/plotOutput'</code><code class="r plain">,value = </code><code class="r string">'tab1'</code><code class="r plain">,</code><code class="r functions">plotOutput</code><code class="r plain">(</code><code class="r string">'p'</code><code class="r plain">)),</code></div>
<div class="line number32 index31 alt1"><code class="r functions">tabPanel</code><code class="r plain">(</code><code class="r string">'ggEdit/ggEditUI'</code><code class="r plain">,value = </code><code class="r string">'tab2'</code><code class="r plain">,</code><code class="r functions">ggEditUI</code><code class="r plain">(</code><code class="r string">'pOut1'</code><code class="r plain">)),</code></div>
<div class="line number33 index32 alt2"><code class="r functions">tabPanel</code><code class="r plain">(</code><code class="r string">'ggEdit/ggEditUI with lists of plots'</code><code class="r plain">,value = </code><code class="r string">'tab3'</code><code class="r plain">,</code><code class="r functions">ggEditUI</code><code class="r plain">(</code><code class="r string">'pOut2'</code><code class="r plain">))</code></div>
<div class="line number34 index33 alt1"><code class="r plain">)))</code></div>
<div class="line number35 index34 alt2"><code class="r functions">shinyApp</code><code class="r plain">(ui, server)</code></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
</div>
<div id="gggedit" class="section level3">
<h3>gggedit</h3>
<a href="http://docs.ggplot2.org/0.9.2.1/ggsave.html" target="_blank" rel="nofollow">ggsave</a> is the device writing function written for the ggplot2 package. A limitation of it is that only one figure can be written at a time. gggsave is a wrapper of ggsave that allows for list of ggplots to be called and then passes arguments to base graphics devices to create multiple outputs automatically, without the need of loops.
<div>
<div id="highlighter_922125" class="syntaxhighlighter  r">
<table border="0" cellspacing="0" cellpadding="0">
<tbody>
<tr>
<td class="gutter">
<div class="line number1 index0 alt2">1</div>
<div class="line number2 index1 alt1">2</div>
<div class="line number3 index2 alt2">3</div>
<div class="line number4 index3 alt1">4</div>
<div class="line number5 index4 alt2">5</div>
<div class="line number6 index5 alt1">6</div>
<div class="line number7 index6 alt2">7</div>
<div class="line number8 index7 alt1">8</div>
<div class="line number9 index8 alt2">9</div></td>
<td class="code">
<div class="container">
<div class="line number1 index0 alt2"><code class="r functions">library</code><code class="r plain">(ggedit) </code></div>
<div class="line number2 index1 alt1"><code class="r comments">#single file output to pdf </code></div>
<div class="line number3 index2 alt2"><code class="r functions">gggsave</code><code class="r plain">(</code><code class="r string">'Rplots.pdf'</code><code class="r plain">,plot=pList) </code></div>
<div class="line number4 index3 alt1"></div>
<div class="line number5 index4 alt2"><code class="r comments">#multiple file output to pdf </code></div>
<div class="line number6 index5 alt1"><code class="r functions">gggsave</code><code class="r plain">(</code><code class="r string">'Rplots.pdf'</code><code class="r plain">,plot=pList,onefil = </code><code class="r keyword">FALSE</code><code class="r plain">) </code></div>
<div class="line number7 index6 alt2"></div>
<div class="line number8 index7 alt1"><code class="r comments">#multiple file output to png </code></div>
<div class="line number9 index8 alt2"><code class="r functions">gggsave</code><code class="r plain">(</code><code class="r string">'Rplots.png'</code><code class="r plain">,plot=pList)</code></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
</div></blockquote>
<blockquote>ggedit is a package that lets users interactively edit ggplot layer and theme aesthetics. In a previous post we showed you how to use it in a collaborative workflow using standard R scripts. More importantly, we highlighted that ggedit outputs to the user, after editing, updated: gg plots, layers, scales and themes as both self-contained … Continue reading ggedit 0.1.1: Shiny module to interactvely edit ggplots within Shiny applications</blockquote>
소스: <em><a href="https://www.r-bloggers.com/ggedit-0-1-1-shiny-module-to-interactvely-edit-ggplots-within-shiny-applications/">ggedit 0.1.1: Shiny module to interactvely edit ggplots within Shiny applications | R-bloggers</a></em>