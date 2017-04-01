---
ID: 1794
post_title: >
  ggedit 0.2.0 is now on CRAN –
  R-posts.com
author: The-R
post_date: 2017-04-01 22:21:39
post_excerpt: ""
layout: post
permalink: >
  http://the-r.kr/2017/04/01/ggedit-0-2-0-is-now-on-cran-r-posts-com/
published: true
inline_featured_image:
  - "0"
---
<img src="http://the-r.kr/wp-content/uploads/2017/04/introPic1.png" alt="ggedit" width="660" height="319" />

We are pleased to announce the release of the ggedit package on <a href="https://cran.r-project.org/web/packages/ggedit/index.html">CRAN</a>.

To install the package you can call the standard R command
<pre><code>install.packages('ggedit')</code></pre>
The source version is still tracked on <a href="https://github.com/metrumresearchgroup/ggedit">github</a>, which has been reorganized to be easier to navigate.

To install the dev version:
<pre><code>devtools::install_github('metrumresearchgroup/ggedit')</code></pre>
<div id="what-is-ggedit" class="section level3">
<h3>What is ggedit?</h3>
ggedit is an R package that is used to facilitate ggplot formatting. With ggedit, R users of all experience levels can easily move from creating ggplots to refining aesthetic details, all while maintaining portability for further reproducible research and collaboration.
ggedit is run from an R console or as a reactive object in any Shiny application. The user inputs a ggplot object or a list of objects. The application populates Bootstrap modals with all of the elements found in each layer, scale, and theme of the ggplot objects. The user can then edit these elements and interact with the plot as changes occur. During editing, a comparison of the script is logged, which can be directly copied and shared. The application output is a nested list containing the edited layers, scales, and themes in both object and script form, so you can apply the edited objects independent of the original plot using regular ggplot2 grammar.
Why does it matter? ggedit promotes efficient collaboration. You can share your plots with team members to make formatting changes, and they can then send any objects they’ve edited back to you for implementation. No more email chains to change a circle to a triangle!

</div>
<div id="updates-in-ggedit-0.2.0" class="section level3">
<h3>Updates in ggedit 0.2.0:</h3>
<ul>
 	<li>The layer modal (popups) elements have been reorganized for less clutter and easier navigation.</li>
 	<li>The S3 method written to plot and compare themes has been removed from the package, but can still be found on the repo, see <a href="https://github.com/metrumresearchgroup/ggedit/blob/master/Miscellaneous/Utilities/plot.theme.R">plot.theme</a>.</li>
</ul>
</div>
<div id="deploying" class="section level3">
<h3>Deploying</h3>
<ul>
 	<li>call from the console: <code>ggedit(p)</code></li>
 	<li>call from the addin toolbar: highlight script of a plot object on the source editor window of RStudio and run from toolbar.</li>
 	<li>call as part of Shiny: use the Shiny module syntax to call the ggEdit UI elements.
<ul>
 	<li>server: <code>callModule(ggEdit,'pUI',obj=reactive(p))</code></li>
 	<li>ui: <code>ggEditUI('pUI')</code></li>
</ul>
</li>
 	<li>if you have installed the package you can see an example of a Shiny app by executing <code>runApp(system.file('examples/shinyModule.R',package = 'ggedit'))</code></li>
</ul>
</div>
<div id="outputs" class="section level3">
<h3>Outputs</h3>
ggedit returns a list containing 8 elements either to the global enviroment or as a reactive output in Shiny.
<ul>
 	<li>updatedPlots
<ul>
 	<li>List containing updated ggplot objects</li>
</ul>
</li>
 	<li>updatedLayers
<ul>
 	<li>For each plot a list of updated layers (ggproto) objects</li>
 	<li>Portable object</li>
</ul>
</li>
 	<li>updatedLayersElements
<ul>
 	<li>For each plot a list elements and their values in each layer</li>
 	<li>Can be used to update the new values in the original code</li>
</ul>
</li>
 	<li>updatedLayerCalls
<ul>
 	<li>For each plot a list of scripts that can be run directly from the console to create a layer</li>
</ul>
</li>
 	<li>updatedThemes
<ul>
 	<li>For each plot a list of updated theme objects</li>
 	<li>Portable object</li>
 	<li>If the user doesn’t edit the theme updatedThemes will not be returned</li>
</ul>
</li>
 	<li>updatedThemeCalls
<ul>
 	<li>For each plot a list of scripts that can be run directly from the console to create a theme</li>
</ul>
</li>
 	<li>updatedScales
<ul>
 	<li>For each plot a list of updated scales (ggproto) objects</li>
 	<li>Portable object</li>
</ul>
</li>
 	<li>updatedScaleCalls
<ul>
 	<li>For each plot a list of scripts that can be run directly from the console to create a scale</li>
</ul>
</li>
</ul>
</div>
<div id="short-clip-to-use-ggedit-in-shiny" class="section level3"></div>
<h3>Short Clip to use ggedit in Shiny</h3>
<a href="https://www.youtube.com/embed/pJ1kbd_OVwg"><img src="http://the-r.kr/wp-content/uploads/2017/04/0.jpg" srcset="http://the-r.kr/wp-content/uploads/2017/04/0.jpg" width="400" height="225" /></a>

<hr />

<em>Jonathan Sidi joined Metrum Research Group in 2016 after working for several years on problems in applied statistics, financial stress testing and economic forecasting in both industrial and academic settings. To learn more about additional open-source software packages developed by Metrum Research Group please visit the Metrum <a href="http://metrumrg.com/opensourcetools.html" target="_blank">website</a>. Contact: For questions and comments, feel free to email me at: yonis@metrumrg.com or open an issue for bug fixes or enhancements at <a href="https://github.com/metrumresearchgroup/ggedit/issues" target="_blank">github</a>.</em>

&nbsp;

소스: <em><a href="http://r-posts.com/ggedit-0-2-0-is-now-on-cran/">ggedit 0.2.0 is now on CRAN – R-posts.com</a></em>