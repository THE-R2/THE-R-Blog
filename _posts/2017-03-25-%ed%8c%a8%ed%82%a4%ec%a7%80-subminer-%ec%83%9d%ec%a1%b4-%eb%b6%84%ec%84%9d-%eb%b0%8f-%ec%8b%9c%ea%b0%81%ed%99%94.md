---
ID: 1770
post_title: '[패키지]  subminer : 생존 분석 및 시각화'
author: The-R
post_date: 2017-03-25 17:44:18
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/03/25/%ed%8c%a8%ed%82%a4%ec%a7%80-subminer-%ec%83%9d%ec%a1%b4-%eb%b6%84%ec%84%9d-%eb%b0%8f-%ec%8b%9c%ea%b0%81%ed%99%94/'
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "3"
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
The <strong>survminer</strong> R package provides functions for facilitating <strong>survival analysis</strong> and <strong>visualization</strong>.

The main functions, in the package, are organized in different categories as follow.

<strong>Survival Curves</strong>

<hr />

<ul>
 	<li><strong>ggsurvplot</strong>(): Draws survival curves with the ‘number at risk’ table and ‘censoring count plot’.</li>
 	<li><strong>arrange_ggsurvplots</strong>(): Arranges multiple ggsurvplots on the same page.</li>
 	<li><strong>ggsurvevents</strong>(): Plots the distribution of event’s times.</li>
 	<li><strong>surv_summary</strong>(): Summary of a survival curve. Compared to the default summary() function, surv_summary() creates a data frame containing a nice summary from survfit results.</li>
 	<li><strong>surv_cutpoint</strong>(): Determines the optimal cutpoint for one or multiple continuous variables at once. Provides a value of a cutpoint that correspond to the most significant relation with survival.</li>
 	<li><strong>pairwise_survdiff</strong>(): Multiple comparisons of survival curves. Calculate pairwise comparisons between group levels with corrections for multiple testing.</li>
</ul>
<strong>Diagnostics of Cox Model</strong>

<hr />

<ul>
 	<li><strong>ggcoxzph</strong>(): Graphical test of proportional hazards. Displays a graph of the scaled Schoenfeld residuals, along with a smooth curve using ggplot2. Wrapper around plot.cox.zph().</li>
 	<li><strong>ggcoxdiagnostics</strong>(): Displays diagnostics graphs presenting goodness of Cox Proportional Hazards Model fit.</li>
 	<li><strong>ggcoxfunctional</strong>(): Displays graphs of continuous explanatory variable against martingale residuals of null cox proportional hazards model. It helps to properly choose the functional form of continuous variable in cox model.</li>
</ul>
<strong>Summary of Cox Model</strong>

<hr />

<ul>
 	<li><strong>ggforest</strong>(): Draws forest plot for CoxPH model.</li>
 	<li><strong>ggcoxadjustedcurves</strong>(): Plots adjusted survival curves for coxph model.</li>
</ul>
<strong>Competing Risks</strong>

<hr />

<ul>
 	<li><strong>ggcompetingrisks</strong>(): Plots cumulative incidence curves for competing risks.</li>
</ul>
<blockquote>Find out more at <a class="uri" href="http://www.sthda.com/english/rpkgs/survminer/">http://www.sthda.com/english/rpkgs/survminer/</a>, and check out the documentation and usage examples of each of the functions in survminer package.</blockquote>
<div id="installation-and-loading" class="section level2">
<h2 class="hasAnchor">Installation and loading</h2>
Install from <a href="https://cran.r-project.org/package=survminer">CRAN</a> as follow:
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">install.packages</span>(<span class="st">"survminer"</span>)</code></pre>
</div>
Or, install the latest version from <a href="https://github.com/kassambara/survminer">GitHub</a>:
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r">if(!<span class="kw">require</span>(devtools)) <span class="kw">install.packages</span>(<span class="st">"devtools"</span>)
devtools::<span class="kw">install_github</span>(<span class="st">"kassambara/survminer"</span>, <span class="dt">build_vignettes =</span> <span class="ot">FALSE</span>)</code></pre>
</div>
Load survminer:
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(<span class="st">"survminer"</span>)</code></pre>
</div>
</div>
<div id="ggsurvplot-drawing-survival-curves" class="section level2">
<h2 class="hasAnchor">ggsurvplot: Drawing survival curves</h2>
<div id="fitting-survival-curves" class="section level3">
<h3 class="hasAnchor">Fitting survival curves</h3>
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">require</span>(<span class="st">"survival"</span>)
fit &lt;- <span class="kw">survfit</span>(<span class="kw">Surv</span>(time, status) ~ sex, <span class="dt">data =</span> lung)</code></pre>
</div>
</div>
<div id="basic-plots" class="section level3">
<h3 class="hasAnchor">Basic plots</h3>
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw"><a href="http://www.sthda.com/english/rpkgs/survminer/reference/ggsurvplot.html">ggsurvplot</a></span>(fit, <span class="dt">data =</span> lung)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/README-ggplot2-basic-survival-plot-1.png" width="480" />

</div>
<div id="customized-survival-curves" class="section level3">
<h3 class="hasAnchor">Customized survival curves</h3>
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw"><a href="http://www.sthda.com/english/rpkgs/survminer/reference/ggsurvplot.html">ggsurvplot</a></span>(fit, <span class="dt">data =</span> lung, <span class="dt">size =</span> <span class="dv">1</span>,  <span class="co"># change line size</span>
           <span class="dt">palette =</span> <span class="kw">c</span>(<span class="st">"#E7B800"</span>, <span class="st">"#2E9FDF"</span>), <span class="co"># custom color palettes</span>
           <span class="dt">conf.int =</span> <span class="ot">TRUE</span>, <span class="co"># Add confidence interval</span>
           <span class="dt">pval =</span> <span class="ot">TRUE</span>, <span class="co"># Add p-value</span>
           <span class="dt">risk.table =</span> <span class="ot">TRUE</span>, <span class="co"># Add risk table</span>
           <span class="dt">risk.table.col =</span> <span class="st">"strata"</span>, <span class="co"># Risk table color by groups</span>
           <span class="dt">legend.labs =</span> <span class="kw">c</span>(<span class="st">"Male"</span>, <span class="st">"Female"</span>), <span class="co"># Change legend labels</span>
           <span class="dt">risk.table.height =</span> <span class="fl">0.25</span>, <span class="co"># Useful to change when you have multiple groups</span>
           <span class="dt">ggtheme =</span> <span class="kw">theme_bw</span>() <span class="co"># Change ggplot2 theme</span>
           )</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/README-ggplot2-customized-survival-plot-1.png" width="576" />

Note that, additional arguments are available to customize the main title, axis labels, the font style, axis limits, legends and the number at risk table.

</div>
<div id="more-customized-survival-curves" class="section level3">
<h3 class="hasAnchor">More customized survival curves</h3>
Focus on <code>xlim</code> and <code>break.time.by</code> parameters which do not change the calculations of estimates of survival surves. Also note <code>risk.table.y.text.col = TRUE</code> and <code>risk.table.y.text = FALSE</code> that provide bars instead of names in text annotations of the legend of risk table.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw"><a href="http://www.sthda.com/english/rpkgs/survminer/reference/ggsurvplot.html">ggsurvplot</a></span>(
   fit,                     <span class="co"># survfit object with calculated statistics.</span>
   <span class="dt">data =</span> lung,             <span class="co"># data used to fit survival curves.</span>
   <span class="dt">risk.table =</span> <span class="ot">TRUE</span>,       <span class="co"># show risk table.</span>
   <span class="dt">pval =</span> <span class="ot">TRUE</span>,             <span class="co"># show p-value of log-rank test.</span>
   <span class="dt">conf.int =</span> <span class="ot">TRUE</span>,         <span class="co"># show confidence intervals for </span>
                            <span class="co"># point estimates of survival curves.</span>
   <span class="dt">xlim =</span> <span class="kw">c</span>(<span class="dv">0</span>,<span class="dv">500</span>),         <span class="co"># present narrower X axis, but not affect</span>
                            <span class="co"># survival estimates.</span>
   <span class="dt">xlab =</span> <span class="st">"Time in days"</span>,   <span class="co"># customize X axis label.</span>
   <span class="dt">break.time.by =</span> <span class="dv">100</span>,     <span class="co"># break X axis in time intervals by 500.</span>
   <span class="dt">ggtheme =</span> <span class="kw">theme_light</span>(), <span class="co"># customize plot and risk table with a theme.</span>
 <span class="dt">risk.table.y.text.col =</span> T, <span class="co"># colour risk table text annotations.</span>
  <span class="dt">risk.table.y.text =</span> <span class="ot">FALSE</span> <span class="co"># show bars instead of names in text annotations</span>
                            <span class="co"># in legend of risk table</span>
)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/README-ggplot2-more-customized-survival-plot-1.png" width="576" />

</div>
<div id="uber-customized-survival-curves" class="section level3">
<h3 class="hasAnchor">Uber customized survival curves</h3>
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r">ggsurv &lt;- <span class="kw"><a href="http://www.sthda.com/english/rpkgs/survminer/reference/ggsurvplot.html">ggsurvplot</a></span>(
           fit,                     <span class="co"># survfit object with calculated statistics.</span>
           <span class="dt">data =</span> lung,             <span class="co"># data used to fit survival curves.</span>
           <span class="dt">risk.table =</span> <span class="ot">TRUE</span>,       <span class="co"># show risk table.</span>
           <span class="dt">pval =</span> <span class="ot">TRUE</span>,             <span class="co"># show p-value of log-rank test.</span>
           <span class="dt">conf.int =</span> <span class="ot">TRUE</span>,         <span class="co"># show confidence intervals for </span>
                                    <span class="co"># point estimates of survival curves.</span>
           <span class="dt">xlim =</span> <span class="kw">c</span>(<span class="dv">0</span>,<span class="dv">500</span>),         <span class="co"># present narrower X axis, but not affect</span>
                                    <span class="co"># survival estimates.</span>
           <span class="dt">xlab =</span> <span class="st">"Time in days"</span>,   <span class="co"># customize X axis label.</span>
           <span class="dt">break.time.by =</span> <span class="dv">100</span>,     <span class="co"># break X axis in time intervals by 500.</span>
           <span class="dt">ggtheme =</span> <span class="kw">theme_light</span>(), <span class="co"># customize plot and risk table with a theme.</span>
          <span class="dt">risk.table.y.text.col =</span> T,<span class="co"># colour risk table text annotations.</span>
          <span class="dt">risk.table.height =</span> <span class="fl">0.25</span>, <span class="co"># the height of the risk table</span>
          <span class="dt">risk.table.y.text =</span> <span class="ot">FALSE</span>,<span class="co"># show bars instead of names in text annotations</span>
                                    <span class="co"># in legend of risk table.</span>
          <span class="dt">ncensor.plot =</span> <span class="ot">TRUE</span>,      <span class="co"># plot the number of censored subjects at time t</span>
          <span class="dt">ncensor.plot.height =</span> <span class="fl">0.25</span>,
          <span class="dt">conf.int.style =</span> <span class="st">"step"</span>,  <span class="co"># customize style of confidence intervals</span>
          <span class="dt">surv.median.line =</span> <span class="st">"hv"</span>,  <span class="co"># add the median survival pointer.</span>
          <span class="dt">legend.labs =</span> 
            <span class="kw">c</span>(<span class="st">"Male"</span>, <span class="st">"Female"</span>)    <span class="co"># change legend labels.</span>
        )

<span class="co"># Apply custom color palettes and print</span>
<span class="kw">ggpar</span>(ggsurv, <span class="dt">palette =</span> <span class="kw">c</span>(<span class="st">"#E7B800"</span>, <span class="st">"#2E9FDF"</span>))</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/README-ggplot2-uber-customized-survival-plot-1.png" width="576" />

</div>
<div id="uber-platinum-customized-survival-curves" class="section level3">
<h3 class="hasAnchor">Uber platinum customized survival curves</h3>
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># Changing Labels</span>
<span class="co"># %%%%%%%%%%%%%%%%%%%%%%%%%%</span>
<span class="co"># Labels for Survival Curves (plot)</span>
ggsurv$plot &lt;- ggsurv$plot + <span class="kw">labs</span>(
  <span class="dt">title =</span> <span class="st">"Survival curves"</span>,                     
  <span class="dt">subtitle =</span> <span class="st">"Based on Kaplan-Meier estimates"</span>,  
  <span class="dt">caption =</span> <span class="st">"created with survminer"</span>             
  )

<span class="co"># Labels for Risk Table </span>
ggsurv$table &lt;- ggsurv$table + <span class="kw">labs</span>(
  <span class="dt">title =</span> <span class="st">"Note the risk set sizes"</span>,          
  <span class="dt">subtitle =</span> <span class="st">"and remember about censoring."</span>, 
  <span class="dt">caption =</span> <span class="st">"source code: website.com"</span>        
  )

<span class="co"># Labels for ncensor plot </span>
ggsurv$ncensor.plot &lt;- ggsurv$ncensor.plot + <span class="kw">labs</span>( 
  <span class="dt">title =</span> <span class="st">"Number of censorings"</span>, 
  <span class="dt">subtitle =</span> <span class="st">"over the time."</span>,
  <span class="dt">caption =</span> <span class="st">"source code: website.com"</span>
  )

<span class="co"># Changing the font size, style and color</span>
<span class="co"># %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%</span>
<span class="co"># Applying the same font style to all the components of ggsurv:</span>
<span class="co"># survival curves, risk table and censor part</span>

ggsurv &lt;- <span class="kw">ggpar</span>(ggsurv,
          <span class="dt">font.title =</span> <span class="kw">c</span>(<span class="dv">16</span>, <span class="st">"bold"</span>, <span class="st">"darkblue"</span>),         
          <span class="dt">font.subtitle =</span> <span class="kw">c</span>(<span class="dv">15</span>, <span class="st">"bold.italic"</span>, <span class="st">"purple"</span>), 
          <span class="dt">font.caption =</span> <span class="kw">c</span>(<span class="dv">14</span>, <span class="st">"plain"</span>, <span class="st">"orange"</span>),        
          <span class="dt">font.x =</span> <span class="kw">c</span>(<span class="dv">14</span>, <span class="st">"bold.italic"</span>, <span class="st">"red"</span>),          
          <span class="dt">font.y =</span> <span class="kw">c</span>(<span class="dv">14</span>, <span class="st">"bold.italic"</span>, <span class="st">"darkred"</span>),      
          <span class="dt">font.tickslab =</span> <span class="kw">c</span>(<span class="dv">12</span>, <span class="st">"plain"</span>, <span class="st">"darkgreen"</span>),
          <span class="dt">legend =</span> <span class="st">"top"</span>
          )

<span class="co"># Apply custom color palettes and print</span>
<span class="kw">ggpar</span>(ggsurv, <span class="dt">palette =</span> <span class="kw">c</span>(<span class="st">"#E7B800"</span>, <span class="st">"#2E9FDF"</span>))</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/README-ggplot2-uber-platinium-customized-survival-plot-1.png" width="576" />

</div>
</div>
<div id="uber-platinum-premium-customized-survival-curves" class="section level2">
<h2 class="hasAnchor">Uber platinum premium customized survival curves</h2>
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># Using specific fonts for risk table and ncensor plots</span>
<span class="co">#%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%</span>
<span class="co"># Font for Risk Table</span>
ggsurv$table &lt;- <span class="kw">ggpar</span>(ggsurv$table,
                      <span class="dt">font.title =</span> <span class="kw">c</span>(<span class="dv">13</span>, <span class="st">"bold.italic"</span>, <span class="st">"green"</span>),
                      <span class="dt">font.subtitle =</span> <span class="kw">c</span>(<span class="dv">15</span>, <span class="st">"bold"</span>, <span class="st">"pink"</span>),
                      <span class="dt">font.caption =</span> <span class="kw">c</span>(<span class="dv">11</span>, <span class="st">"plain"</span>, <span class="st">"darkgreen"</span>),
                      <span class="dt">font.x =</span> <span class="kw">c</span>(<span class="dv">8</span>, <span class="st">"bold.italic"</span>, <span class="st">"orange"</span>),
                      <span class="dt">font.y =</span> <span class="kw">c</span>(<span class="dv">11</span>, <span class="st">"bold.italic"</span>, <span class="st">"darkgreen"</span>),
                      <span class="dt">font.tickslab =</span> <span class="kw">c</span>(<span class="dv">9</span>, <span class="st">"bold"</span>, <span class="st">"red"</span>)
                      )


<span class="co"># Font for ncensor plot</span>
ggsurv$ncensor.plot &lt;- <span class="kw">ggpar</span>(ggsurv$ncensor.plot,
                            <span class="dt">font.title =</span> <span class="kw">c</span>(<span class="dv">13</span>, <span class="st">"bold.italic"</span>, <span class="st">"green"</span>),
                            <span class="dt">font.subtitle =</span> <span class="kw">c</span>(<span class="dv">15</span>, <span class="st">"bold"</span>, <span class="st">"pink"</span>),
                            <span class="dt">font.caption =</span> <span class="kw">c</span>(<span class="dv">11</span>, <span class="st">"plain"</span>, <span class="st">"darkgreen"</span>),
                            <span class="dt">font.x =</span> <span class="kw">c</span>(<span class="dv">8</span>, <span class="st">"bold.italic"</span>, <span class="st">"orange"</span>),
                            <span class="dt">font.y =</span> <span class="kw">c</span>(<span class="dv">11</span>, <span class="st">"bold.italic"</span>, <span class="st">"darkgreen"</span>),
                            <span class="dt">font.tickslab =</span> <span class="kw">c</span>(<span class="dv">9</span>, <span class="st">"bold"</span>, <span class="st">"red"</span>)
                            )

<span class="kw">print</span>(ggsurv)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/README-ggplot2-uber-platinium-premium-customized-survival-plot-1.png" width="576" />

</div>
<div id="blog-posts" class="section level2">
<h2 class="hasAnchor">Blog posts</h2>
<ul>
 	<li>M. Kosiński. R-ADDICT January 2017. <a href="http://r-addict.com/2017/02/09/Fancy-Survival-Plots.html">Comparing (Fancy) Survival Curves with Weighted Log-rank Tests</a></li>
 	<li>M. Kosiński. R-ADDICT January 2017. <a href="http://r-addict.com/2017/01/15/Too-Far-With-Survival-Plots.html">When You Went too Far with Survival Plots During the survminer 1st Anniversary</a></li>
 	<li>A. Kassambara. STHDA December 2016. <a href="http://www.sthda.com/english/wiki/survival-analysis-basics">Survival Analysis Basics: Curves and Logrank Tests</a></li>
 	<li>A. Kassambara. STHDA December 2016. <a href="http://www.sthda.com/english/wiki/cox-proportional-hazards-model">Cox Proportional Hazards Model</a></li>
 	<li>A. Kassambara. STHDA December 2016. <a href="http://www.sthda.com/english/wiki/cox-model-assumptions">Cox Model Assumptions</a></li>
 	<li>M. Kosiński. R-ADDICT November 2016. <a href="http://r-addict.com/2016/11/21/Optimal-Cutpoint-maxstat.html">Determine optimal cutpoints for numerical variables in survival plots</a></li>
 	<li>M. Kosiński. R-ADDICT May 2016. <a href="http://r-addict.com/2016/05/23/Informative-Survival-Plots.html">Survival plots have never been so informative</a></li>
 	<li>A. Kassambara. STHDA January 2016. <a href="http://www.sthda.com/english/wiki/survminer-r-package-survival-data-analysis-and-visualization">survminer R package: Survival Data Analysis and Visualization</a>.</li>
</ul>
</div>
소스: <em><a href="http://www.sthda.com/english/rpkgs/survminer/#installation-and-loading">Drawing Survival Curves using 'ggplot2' • survminer</a></em>