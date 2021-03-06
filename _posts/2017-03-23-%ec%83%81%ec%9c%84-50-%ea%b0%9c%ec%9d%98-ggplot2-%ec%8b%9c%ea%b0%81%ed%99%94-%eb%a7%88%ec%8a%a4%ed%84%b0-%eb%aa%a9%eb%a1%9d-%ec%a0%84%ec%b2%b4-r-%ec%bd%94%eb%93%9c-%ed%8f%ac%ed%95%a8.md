---
ID: 1702
post_title: '상위 50 개의 ggplot2 시각화 &#8211; 마스터 목록 (전체 R 코드 포함)'
author: The-R
post_date: 2017-03-23 18:18:14
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/03/23/%ec%83%81%ec%9c%84-50-%ea%b0%9c%ec%9d%98-ggplot2-%ec%8b%9c%ea%b0%81%ed%99%94-%eb%a7%88%ec%8a%a4%ed%84%b0-%eb%aa%a9%eb%a1%9d-%ec%a0%84%ec%b2%b4-r-%ec%bd%94%eb%93%9c-%ed%8f%ac%ed%95%a8/'
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "3"
scc_share_count_google+:
  - "0"
scc_share_count_facebook:
  - "-1"
scc_share_count_pocket:
  - "0"
scc_share_count_hatebu:
  - "0"
scc_share_count_crawldate:
  - 2017/03/24 10:16:03
scc_share_count_total:
  - "0"
slide_template:
  - default
sbg_selected_sidebar:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_replacement:
  - 'a:1:{i:0;s:0:"";}'
sbg_selected_sidebar_2:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_2_replacement:
  - 'a:1:{i:0;s:0:"";}'
pyre_show_first_featured_image:
  - 'no'
pyre_fimg_width:
  - ""
pyre_fimg_height:
  - ""
pyre_portfolio_width_100:
  - default
pyre_video:
  - ""
pyre_image_rollover_icons:
  - default
pyre_link_icon_url:
  - ""
pyre_post_links_target:
  - 'no'
pyre_related_posts:
  - default
pyre_share_box:
  - default
pyre_post_pagination:
  - default
pyre_author_info:
  - default
pyre_post_meta:
  - default
pyre_post_comments:
  - default
pyre_main_top_padding:
  - ""
pyre_main_bottom_padding:
  - ""
pyre_hundredp_padding:
  - ""
pyre_slider_type:
  - 'no'
pyre_slider:
  - "0"
pyre_wooslider:
  - "0"
pyre_revslider:
  - "0"
pyre_elasticslider:
  - "0"
pyre_slider_position:
  - default
pyre_avada_rev_styles:
  - default
pyre_fallback:
  - ""
pyre_demo_slider:
  - ""
pyre_display_header:
  - 'yes'
pyre_header_100_width:
  - default
pyre_header_bg_color:
  - ""
pyre_header_bg_opacity:
  - ""
pyre_header_bg:
  - ""
pyre_header_bg_full:
  - 'no'
pyre_header_bg_repeat:
  - repeat
pyre_displayed_menu:
  - default
pyre_display_footer:
  - default
pyre_display_copyright:
  - default
pyre_footer_100_width:
  - default
pyre_sidebar_position:
  - default
pyre_sidebar_bg_color:
  - ""
pyre_page_bg_layout:
  - default
pyre_page_bg_color:
  - ""
pyre_page_bg:
  - ""
pyre_page_bg_full:
  - 'no'
pyre_page_bg_repeat:
  - repeat
pyre_wide_page_bg_color:
  - ""
pyre_wide_page_bg:
  - ""
pyre_wide_page_bg_full:
  - 'no'
pyre_wide_page_bg_repeat:
  - repeat
pyre_page_title:
  - default
pyre_page_title_breadcrumbs_search_bar:
  - default
pyre_page_title_text:
  - default
pyre_page_title_text_alignment:
  - default
pyre_page_title_custom_text:
  - ""
pyre_page_title_text_size:
  - ""
pyre_page_title_custom_subheader:
  - ""
pyre_page_title_custom_subheader_text_size:
  - ""
pyre_page_title_font_color:
  - ""
pyre_page_title_100_width:
  - default
pyre_page_title_height:
  - ""
pyre_page_title_mobile_height:
  - ""
pyre_page_title_bar_bg_color:
  - ""
pyre_page_title_bar_borders_color:
  - ""
pyre_page_title_bar_bg:
  - ""
pyre_page_title_bar_bg_retina:
  - ""
pyre_page_title_bar_bg_full:
  - default
pyre_page_title_bg_parallax:
  - default
fusion_builder_status:
  - ""
---
<h2>상위 50 개의 ggplot2 시각화 - 마스터 목록 (전체 R 코드 포함)</h2>
<blockquote>What type of visualization to use for what sort of problem? This tutorial helps you choose the right type of chart for your specific objectives and how to implement it in R using ggplot2.</blockquote>
This is part 3 of a three part tutorial on ggplot2, an aesthetically pleasing (and very popular) graphics framework in R. This tutorial is primarily geared towards those having some basic knowledge of the R programming language and want to make complex and nice looking charts with R ggplot2.
<ul>
 	<li><a href="http://r-statistics.co/Complete-Ggplot2-Tutorial-Part1-With-R-Code.html">Part 1: Introduction to ggplot2</a>, covers the basic knowledge about constructing simple ggplots and modifying the components and aesthetics.</li>
 	<li><a href="http://r-statistics.co/Complete-Ggplot2-Tutorial-Part2-Customizing-Theme-With-R-Code.html">Part 2: Customizing the Look and Feel</a>, is about more advanced customization like manipulating legend, annotations, multiplots with faceting and custom layouts</li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html">Part 3: Top 50 ggplot2 Visualizations - The Master List</a>, applies what was learnt in part 1 and 2 to construct other types of ggplots such as bar charts, boxplots etc.</li>
</ul>
<h3><a name="top"></a>Top 50 ggplot2 Visualizations - The Master List</h3>
An effective chart is one that:
<ol>
 	<li>Conveys the right information without distorting facts.</li>
 	<li>Is simple but elegant. It should not force you to think much in order to get it.</li>
 	<li>Aesthetics supports information rather that overshadow it.</li>
 	<li>Is not overloaded with information.</li>
</ol>
The list below sorts the visualizations based on its primary purpose. Primarily, there are 8 types of objectives you may construct plots. So, before you actually make the plot, try and figure what findings and relationships you would like to convey or examine through the visualization. Chances are it will fall under one (or sometimes more) of these 8 categories.
<ol>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#1.%20Correlation">Correlation</a>
<ul>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Scatterplot">Scatterplot</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Scatterplot%20With%20Encircling">Scatterplot With Encircling</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Jitter%20Plot">Jitter Plot</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Counts%20Chart">Counts Chart</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Bubble%20Plot">Bubble Plot</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Animated%20Bubble%20Plot">Animated Bubble Plot</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Marginal%20Histogram%20/%20Boxplot">Marginal Histogram / Boxplot</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Correlogram">Correlogram</a></li>
</ul>
</li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#2.%20Deviation">Deviation</a>
<ul>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Diverging%20Bars">Diverging Bars</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Diverging%20Lollipop%20Chart">Diverging Lollipop Chart</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Diverging%20Dot%20Plot">Diverging Dot Plot</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Area%20Chart">Area Chart</a></li>
</ul>
</li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#3.%20Ranking">Ranking</a>
<ul>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Ordered%20Bar%20Chart">Ordered Bar Chart</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Lollipop%20Chart">Lollipop Chart</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Dot%20Plot">Dot Plot</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Slope%20Chart">Slope Chart</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Dumbbell%20Plot">Dumbbell Plot</a></li>
</ul>
</li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#4.%20Distribution">Distribution</a>
<ul>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Histogram">Histogram</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Density%20Plot">Density Plot</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Box%20Plot">Box Plot</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Dot%20+%20Box%20Plot">Dot + Box Plot</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Tufte%20Boxplot">Tufte Boxplot</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Violin%20Plot">Violin Plot</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Population%20Pyramid">Population Pyramid</a></li>
</ul>
</li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#5.%20Composition">Composition</a>
<ul>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Waffle%20Chart">Waffle Chart</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Pie%20Chart">Pie Chart</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Treemap">Treemap</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Bar%20Chart">Bar Chart</a></li>
</ul>
</li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#6.%20Change">Change</a>
<ul>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Time%20Series%20Plot%20From%20a%20Time%20Series%20Object">Time Series Plots</a>
<ul>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Time%20Series%20Plot%20From%20a%20Data%20Frame">From a Data Frame</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Time%20Series%20Plot%20For%20a%20Monthly%20Time%20Series">Format to Monthly X Axis</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Time%20Series%20Plot%20For%20a%20Yearly%20Time%20Series">Format to Yearly X Axis</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Time%20Series%20Plot%20From%20Long%20Data%20Format">From Long Data Format</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Time%20Series%20Plot%20From%20Wide%20Data%20Format">From Wide Data Format</a></li>
</ul>
</li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Stacked%20Area%20Chart">Stacked Area Chart</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Calendar%20Heat%20Map">Calendar Heat Map</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Slope%20Chart%202">Slope Chart</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Seasonal%20Plot">Seasonal Plot</a></li>
</ul>
</li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#7.%20Groups">Groups</a>
<ul>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Hierarchical%20Dendrogram">Dendrogram</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Clusters">Clusters</a></li>
</ul>
</li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#8.%20Spatial">Spatial</a>
<ul>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Open%20Street%20Map">Open Street Map</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Google%20Road%20Map">Google Road Map</a></li>
 	<li><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Google%20Hybrid%20Map">Google Hybrid Map</a></li>
</ul>
</li>
</ol>
<h2 id="1. Correlation">1. Correlation</h2>
The following plots help to examine how well correlated two variables are.
<h3><a name="Scatterplot"></a>Scatterplot</h3>
The most frequently used plot for data analysis is undoubtedly the scatterplot. Whenever you want to understand the nature of relationship between two variables, invariably the first choice is the scatterplot.

It can be drawn using <code>geom_point()</code>. Additionally, <code>geom_smooth</code> which draws a smoothing line (based on loess) by default, can be tweaked to draw the line of best fit by setting <code>method='lm'</code>.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># install.packages("ggplot2")</span>
<span class="co"># load package and data</span>
<span class="kw">options</span>(<span class="dt">scipen=</span><span class="dv">999</span>)  <span class="co"># turn-off scientific notation like 1e+48</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())  <span class="co"># pre-set the bw theme.</span>
<span class="kw">data</span>(<span class="st">"midwest"</span>, <span class="dt">package =</span> <span class="st">"ggplot2"</span>)
<span class="co"># midwest &lt;- read.csv("http://goo.gl/G1K41K")  # bkup data source</span>

<span class="co"># Scatterplot</span>
gg &lt;- <span class="kw">ggplot</span>(midwest, <span class="kw">aes</span>(<span class="dt">x=</span>area, <span class="dt">y=</span>poptotal)) + 
  <span class="kw">geom_point</span>(<span class="kw">aes</span>(<span class="dt">col=</span>state, <span class="dt">size=</span>popdensity)) + 
  <span class="kw">geom_smooth</span>(<span class="dt">method=</span><span class="st">"loess"</span>, <span class="dt">se=</span>F) + 
  <span class="kw">xlim</span>(<span class="kw">c</span>(<span class="dv">0</span>, <span class="fl">0.1</span>)) + 
  <span class="kw">ylim</span>(<span class="kw">c</span>(<span class="dv">0</span>, <span class="dv">500000</span>)) + 
  <span class="kw">labs</span>(<span class="dt">subtitle=</span><span class="st">"Area Vs Population"</span>, 
       <span class="dt">y=</span><span class="st">"Population"</span>, 
       <span class="dt">x=</span><span class="st">"Area"</span>, 
       <span class="dt">title=</span><span class="st">"Scatterplot"</span>, 
       <span class="dt">caption =</span> <span class="st">"Source: midwest"</span>)

<span class="kw">plot</span>(gg)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_1.png" alt="ggplot2 Scatterplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Scatterplot With Encircling"></a>Scatterplot With Encircling</h3>
When presenting the results, sometimes I would encirlce certain special group of points or region in the chart so as to draw the attention to those peculiar cases. This can be conveniently done using the <code>geom_encircle()</code> in <code>ggalt</code> package.

Within <code>geom_encircle()</code>, set the <code>data</code> to a new dataframe that contains only the points (rows) or interest. Moreover, You can <code>expand</code> the curve so as to pass just outside the points. The <code>color</code> and <code>size</code>(thickness) of the curve can be modified as well. See below example.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># install 'ggalt' pkg</span>
<span class="co"># devtools::install_github("hrbrmstr/ggalt")</span>
<span class="kw">options</span>(<span class="dt">scipen =</span> <span class="dv">999</span>)
<span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(ggalt)
midwest_select &lt;- midwest[midwest$poptotal &gt; <span class="dv">350000</span> &amp; 
                            midwest$poptotal &lt;= <span class="dv">500000</span> &amp; 
                            midwest$area &gt; <span class="fl">0.01</span> &amp; 
                            midwest$area &lt; <span class="fl">0.1</span>, ]

<span class="co"># Plot</span>
<span class="kw">ggplot</span>(midwest, <span class="kw">aes</span>(<span class="dt">x=</span>area, <span class="dt">y=</span>poptotal)) + 
  <span class="kw">geom_point</span>(<span class="kw">aes</span>(<span class="dt">col=</span>state, <span class="dt">size=</span>popdensity)) +   <span class="co"># draw points</span>
  <span class="kw">geom_smooth</span>(<span class="dt">method=</span><span class="st">"loess"</span>, <span class="dt">se=</span>F) + 
  <span class="kw">xlim</span>(<span class="kw">c</span>(<span class="dv">0</span>, <span class="fl">0.1</span>)) + 
  <span class="kw">ylim</span>(<span class="kw">c</span>(<span class="dv">0</span>, <span class="dv">500000</span>)) +   <span class="co"># draw smoothing line</span>
  <span class="kw">geom_encircle</span>(<span class="kw">aes</span>(<span class="dt">x=</span>area, <span class="dt">y=</span>poptotal), 
                <span class="dt">data=</span>midwest_select, 
                <span class="dt">color=</span><span class="st">"red"</span>, 
                <span class="dt">size=</span><span class="dv">2</span>, 
                <span class="dt">expand=</span><span class="fl">0.08</span>) +   <span class="co"># encircle</span>
  <span class="kw">labs</span>(<span class="dt">subtitle=</span><span class="st">"Area Vs Population"</span>, 
       <span class="dt">y=</span><span class="st">"Population"</span>, 
       <span class="dt">x=</span><span class="st">"Area"</span>, 
       <span class="dt">title=</span><span class="st">"Scatterplot + Encircle"</span>, 
       <span class="dt">caption=</span><span class="st">"Source: midwest"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_2.png" alt="ggplot2 Scatterplot With Encircling" /><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Jitter Plot"></a>Jitter Plot</h3>
Let’s look at a new data to draw the scatterplot. This time, I will use the <code>mpg</code> dataset to plot city mileage (<code>cty</code>) vs highway mileage (<code>hwy</code>).
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># load package and data</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">data</span>(mpg, <span class="dt">package=</span><span class="st">"ggplot2"</span>) <span class="co"># alternate source: "http://goo.gl/uEeRGu")</span>
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())  <span class="co"># pre-set the bw theme.</span>

g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(cty, hwy))

<span class="co"># Scatterplot</span>
g + <span class="kw">geom_point</span>() + 
  <span class="kw">geom_smooth</span>(<span class="dt">method=</span><span class="st">"lm"</span>, <span class="dt">se=</span>F) +
  <span class="kw">labs</span>(<span class="dt">subtitle=</span><span class="st">"mpg: city vs highway mileage"</span>, 
       <span class="dt">y=</span><span class="st">"hwy"</span>, 
       <span class="dt">x=</span><span class="st">"cty"</span>, 
       <span class="dt">title=</span><span class="st">"Scatterplot with overlapping points"</span>, 
       <span class="dt">caption=</span><span class="st">"Source: midwest"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_3.png" alt="ggplot2 Scatterplot With Hidden Data points" />

What we have here is a scatterplot of city and highway mileage in <code>mpg</code> dataset. We have seen a similar scatterplot and this looks neat and gives a clear idea of how the city mileage (<code>cty</code>) and highway mileage (<code>hwy</code>) are well correlated.

But, this innocent looking plot is <em>hiding</em> something. Can you find out?
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">dim</span>(mpg)</code></pre>
</div>
The original data has 234 data points but the chart seems to display fewer points. What has happened? This is because there are many overlapping points appearing as a single dot. The fact that both <code>cty</code> and <code>hwy</code> are integers in the source dataset made it all the more convenient to hide this detail. So just be extra careful the next time you make scatterplot with integers.

So how to handle this? There are few options. We can make a jitter plot with <code>jitter_geom()</code>. As the name suggests, the overlapping points are randomly jittered around its original position based on a threshold controlled by the <code>width</code> argument.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># load package and data</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">data</span>(mpg, <span class="dt">package=</span><span class="st">"ggplot2"</span>)
<span class="co"># mpg &lt;- read.csv("http://goo.gl/uEeRGu")</span>

<span class="co"># Scatterplot</span>
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())  <span class="co"># pre-set the bw theme.</span>
g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(cty, hwy))
g + <span class="kw">geom_jitter</span>(<span class="dt">width =</span> .<span class="dv">5</span>, <span class="dt">size=</span><span class="dv">1</span>) +
  <span class="kw">labs</span>(<span class="dt">subtitle=</span><span class="st">"mpg: city vs highway mileage"</span>, 
       <span class="dt">y=</span><span class="st">"hwy"</span>, 
       <span class="dt">x=</span><span class="st">"cty"</span>, 
       <span class="dt">title=</span><span class="st">"Jittered Points"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_4.png" alt="ggplot2 Jitter Plot" /> More points are revealed now. More the <code>width</code>, more the points are moved jittered from their original position.

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Counts Chart"></a>Counts Chart</h3>
The second option to overcome the problem of data points overlap is to use what is called a <em>counts chart</em>. Whereever there is more points overlap, the size of the circle gets bigger.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># load package and data</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">data</span>(mpg, <span class="dt">package=</span><span class="st">"ggplot2"</span>)
<span class="co"># mpg &lt;- read.csv("http://goo.gl/uEeRGu")</span>

<span class="co"># Scatterplot</span>
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())  <span class="co"># pre-set the bw theme.</span>
g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(cty, hwy))
g + <span class="kw">geom_count</span>(<span class="dt">col=</span><span class="st">"tomato3"</span>, <span class="dt">show.legend=</span>F) +
  <span class="kw">labs</span>(<span class="dt">subtitle=</span><span class="st">"mpg: city vs highway mileage"</span>, 
       <span class="dt">y=</span><span class="st">"hwy"</span>, 
       <span class="dt">x=</span><span class="st">"cty"</span>, 
       <span class="dt">title=</span><span class="st">"Counts Plot"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_5.png" alt="ggplot2 Counts Plot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Bubble Plot"></a>Bubble plot</h3>
While scatterplot lets you compare the relationship between 2 continuous variables, bubble chart serves well if you want to understand relationship within the underlying groups based on:
<ol>
 	<li>A Categorical variable (by changing the color) and</li>
 	<li>Another continuous variable (by changing the size of points).</li>
</ol>
In simpler words, bubble charts are more suitable if you have 4-Dimensional data where two of them are numeric (X and Y) and one other categorical (color) and another numeric variable (size).

The bubble chart clearly distinguishes the range of <code>displ</code> between the manufacturers and how the slope of lines-of-best-fit varies, providing a better visual comparison between the groups.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># load package and data</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">data</span>(mpg, <span class="dt">package=</span><span class="st">"ggplot2"</span>)
<span class="co"># mpg &lt;- read.csv("http://goo.gl/uEeRGu")</span>

mpg_select &lt;- mpg[mpg$manufacturer %in% <span class="kw">c</span>(<span class="st">"audi"</span>, <span class="st">"ford"</span>, <span class="st">"honda"</span>, <span class="st">"hyundai"</span>), ]

<span class="co"># Scatterplot</span>
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())  <span class="co"># pre-set the bw theme.</span>
g &lt;- <span class="kw">ggplot</span>(mpg_select, <span class="kw">aes</span>(displ, cty)) + 
  <span class="kw">labs</span>(<span class="dt">subtitle=</span><span class="st">"mpg: Displacement vs City Mileage"</span>,
       <span class="dt">title=</span><span class="st">"Bubble chart"</span>)

g + <span class="kw">geom_jitter</span>(<span class="kw">aes</span>(<span class="dt">col=</span>manufacturer, <span class="dt">size=</span>hwy)) + 
  <span class="kw">geom_smooth</span>(<span class="kw">aes</span>(<span class="dt">col=</span>manufacturer), <span class="dt">method=</span><span class="st">"lm"</span>, <span class="dt">se=</span>F)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_6.png" alt="ggplot2 Bubble Plot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Animated Bubble Plot"></a>Animated Bubble chart</h3>
An animated bubble chart can be implemented using the <code>gganimate</code> package. It is same as the bubble chart, but, you have to show how the values change over a fifth dimension (typically time).

The key thing to do is to set the <code>aes(frame)</code> to the desired column on which you want to animate. Rest of the procedure related to plot construction is the same. Once the plot is constructed, you can animate it using <code>gganimate()</code> by setting a chosen <code>interval</code>.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># Source: https://github.com/dgrtwo/gganimate</span>
<span class="co"># install.packages("cowplot")  # a gganimate dependency</span>
<span class="co"># devtools::install_github("dgrtwo/gganimate")</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(gganimate)
<span class="kw">library</span>(gapminder)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())  <span class="co"># pre-set the bw theme.</span>

g &lt;- <span class="kw">ggplot</span>(gapminder, <span class="kw">aes</span>(gdpPercap, lifeExp, <span class="dt">size =</span> pop, <span class="dt">frame =</span> year)) +
  <span class="kw">geom_point</span>() +
  <span class="kw">geom_smooth</span>(<span class="kw">aes</span>(<span class="dt">group =</span> year), 
              <span class="dt">method =</span> <span class="st">"lm"</span>, 
              <span class="dt">show.legend =</span> <span class="ot">FALSE</span>) +
  <span class="kw">facet_wrap</span>(~continent, <span class="dt">scales =</span> <span class="st">"free"</span>) +
  <span class="kw">scale_x_log10</span>()  <span class="co"># convert to log scale</span>

<span class="kw">gganimate</span>(g, <span class="dt">interval=</span><span class="fl">0.2</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_7.gif" alt="ggplot2 Animated Bubble Plot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Marginal Histogram / Boxplot"></a>Marginal Histogram / Boxplot</h3>
If you want to show the relationship as well as the distribution in the same chart, use the marginal histogram. It has a histogram of the X and Y variables at the margins of the scatterplot.

This can be implemented using the <code>ggMarginal()</code> function from the ‘<code>ggExtra</code>’ package. Apart from a <code>histogram</code>, you could choose to draw a marginal <code>boxplot</code> or <code>density</code> plot by setting the respective <code>type</code>option.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># load package and data</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(ggExtra)
<span class="kw">data</span>(mpg, <span class="dt">package=</span><span class="st">"ggplot2"</span>)
<span class="co"># mpg &lt;- read.csv("http://goo.gl/uEeRGu")</span>

<span class="co"># Scatterplot</span>
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())  <span class="co"># pre-set the bw theme.</span>
mpg_select &lt;- mpg[mpg$hwy &gt;= <span class="dv">35</span> &amp; mpg$cty &gt; <span class="dv">27</span>, ]
g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(cty, hwy)) + 
  <span class="kw">geom_count</span>() + 
  <span class="kw">geom_smooth</span>(<span class="dt">method=</span><span class="st">"lm"</span>, <span class="dt">se=</span>F)

<span class="kw">ggMarginal</span>(g, <span class="dt">type =</span> <span class="st">"histogram"</span>, <span class="dt">fill=</span><span class="st">"transparent"</span>)
<span class="kw">ggMarginal</span>(g, <span class="dt">type =</span> <span class="st">"boxplot"</span>, <span class="dt">fill=</span><span class="st">"transparent"</span>)
<span class="co"># ggMarginal(g, type = "density", fill="transparent")</span></code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_8_1.png" alt="ggplot2 Marginal Histogram" />

<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_8_2.png" alt="ggplot2 Marginal Histogram" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Correlogram"></a>Correlogram</h3>
Correlogram let’s you examine the corellation of multiple continuous variables present in the same dataframe. This is conveniently implemented using the <code>ggcorrplot</code> package.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># devtools::install_github("kassambara/ggcorrplot")</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(ggcorrplot)

<span class="co"># Correlation matrix</span>
<span class="kw">data</span>(mtcars)
corr &lt;- <span class="kw">round</span>(<span class="kw">cor</span>(mtcars), <span class="dv">1</span>)

<span class="co"># Plot</span>
<span class="kw">ggcorrplot</span>(corr, <span class="dt">hc.order =</span> <span class="ot">TRUE</span>, 
           <span class="dt">type =</span> <span class="st">"lower"</span>, 
           <span class="dt">lab =</span> <span class="ot">TRUE</span>, 
           <span class="dt">lab_size =</span> <span class="dv">3</span>, 
           <span class="dt">method=</span><span class="st">"circle"</span>, 
           <span class="dt">colors =</span> <span class="kw">c</span>(<span class="st">"tomato2"</span>, <span class="st">"white"</span>, <span class="st">"springgreen3"</span>), 
           <span class="dt">title=</span><span class="st">"Correlogram of mtcars"</span>, 
           <span class="dt">ggtheme=</span>theme_bw)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_9.png" alt="ggplot2 Correlogram" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h2 id="2. Deviation">2. Deviation</h2>
Compare variation in <em>values</em> between small number of items (or categories) with respect to a fixed reference.
<h3><a name="Diverging Bars"></a>Diverging bars</h3>
Diverging Bars is a bar chart that can handle both negative and positive values. This can be implemented by a smart tweak with <code>geom_bar()</code>. But the usage of <code>geom_bar()</code> can be quite confusing. Thats because, it can be used to make a bar chart as well as a histogram. Let me explain.

By default, <code>geom_bar()</code> has the <code>stat</code> set to <code>count</code>. That means, when you provide just a continuous X variable (and no Y variable), it tries to make a histogram out of the data.

In order to make a bar chart create bars instead of histogram, you need to do two things.
<ol>
 	<li>Set <code>stat=identity</code></li>
 	<li>Provide both <code>x</code> and <code>y</code> inside <code>aes()</code> where, <code>x</code> is either <code>character</code> or <code>factor</code> and <code>y</code> is numeric.</li>
</ol>
In order to make sure you get diverging bars instead of just bars, make sure, your categorical variable has 2 categories that changes values at a certain threshold of the continuous variable. In below example, the <code>mpg</code> from mtcars dataset is normalised by computing the z score. Those vehicles with mpg above zero are marked green and those below are marked red.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())  

<span class="co"># Data Prep</span>
<span class="kw">data</span>(<span class="st">"mtcars"</span>)  <span class="co"># load data</span>
mtcars$<span class="st">`</span><span class="dt">car name</span><span class="st">`</span> &lt;- <span class="kw">rownames</span>(mtcars)  <span class="co"># create new column for car names</span>
mtcars$mpg_z &lt;- <span class="kw">round</span>((mtcars$mpg - <span class="kw">mean</span>(mtcars$mpg))/<span class="kw">sd</span>(mtcars$mpg), <span class="dv">2</span>)  <span class="co"># compute normalized mpg</span>
mtcars$mpg_type &lt;- <span class="kw">ifelse</span>(mtcars$mpg_z &lt; <span class="dv">0</span>, <span class="st">"below"</span>, <span class="st">"above"</span>)  <span class="co"># above / below avg flag</span>
mtcars &lt;- mtcars[<span class="kw">order</span>(mtcars$mpg_z), ]  <span class="co"># sort</span>
mtcars$<span class="st">`</span><span class="dt">car name</span><span class="st">`</span> &lt;- <span class="kw">factor</span>(mtcars$<span class="st">`</span><span class="dt">car name</span><span class="st">`</span>, <span class="dt">levels =</span> mtcars$<span class="st">`</span><span class="dt">car name</span><span class="st">`</span>)  <span class="co"># convert to factor to retain sorted order in plot.</span>

<span class="co"># Diverging Barcharts</span>
<span class="kw">ggplot</span>(mtcars, <span class="kw">aes</span>(<span class="dt">x=</span><span class="st">`</span><span class="dt">car name</span><span class="st">`</span>, <span class="dt">y=</span>mpg_z, <span class="dt">label=</span>mpg_z)) + 
  <span class="kw">geom_bar</span>(<span class="dt">stat=</span><span class="st">'identity'</span>, <span class="kw">aes</span>(<span class="dt">fill=</span>mpg_type), <span class="dt">width=</span>.<span class="dv">5</span>)  +
  <span class="kw">scale_fill_manual</span>(<span class="dt">name=</span><span class="st">"Mileage"</span>, 
                    <span class="dt">labels =</span> <span class="kw">c</span>(<span class="st">"Above Average"</span>, <span class="st">"Below Average"</span>), 
                    <span class="dt">values =</span> <span class="kw">c</span>(<span class="st">"above"</span>=<span class="st">"#00ba38"</span>, <span class="st">"below"</span>=<span class="st">"#f8766d"</span>)) + 
  <span class="kw">labs</span>(<span class="dt">subtitle=</span><span class="st">"Normalised mileage from 'mtcars'"</span>, 
       <span class="dt">title=</span> <span class="st">"Diverging Bars"</span>) + 
  <span class="kw">coord_flip</span>()</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_10.png" alt="ggplot2 Diverging Bars" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Diverging Lollipop Chart"></a>Diverging Lollipop Chart</h3>
Lollipop chart conveys the same information as bar chart and diverging bar. Except that it looks more modern. Instead of geom_bar, I use <code>geom_point</code> and <code>geom_segment</code> to get the lollipops right. Let’s draw a lollipop using the same data I prepared in the previous example of diverging bars.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())

<span class="kw">ggplot</span>(mtcars, <span class="kw">aes</span>(<span class="dt">x=</span><span class="st">`</span><span class="dt">car name</span><span class="st">`</span>, <span class="dt">y=</span>mpg_z, <span class="dt">label=</span>mpg_z)) + 
  <span class="kw">geom_point</span>(<span class="dt">stat=</span><span class="st">'identity'</span>, <span class="dt">fill=</span><span class="st">"black"</span>, <span class="dt">size=</span><span class="dv">6</span>)  +
  <span class="kw">geom_segment</span>(<span class="kw">aes</span>(<span class="dt">y =</span> <span class="dv">0</span>, 
                   <span class="dt">x =</span> <span class="st">`</span><span class="dt">car name</span><span class="st">`</span>, 
                   <span class="dt">yend =</span> mpg_z, 
                   <span class="dt">xend =</span> <span class="st">`</span><span class="dt">car name</span><span class="st">`</span>), 
               <span class="dt">color =</span> <span class="st">"black"</span>) +
  <span class="kw">geom_text</span>(<span class="dt">color=</span><span class="st">"white"</span>, <span class="dt">size=</span><span class="dv">2</span>) +
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Diverging Lollipop Chart"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Normalized mileage from 'mtcars': Lollipop"</span>) + 
  <span class="kw">ylim</span>(-<span class="fl">2.5</span>, <span class="fl">2.5</span>) +
  <span class="kw">coord_flip</span>()</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_11.png" alt="ggplot2 Lollipop Plot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Diverging Dot Plot"></a>Diverging Dot Plot</h3>
Dot plot conveys similar information. The principles are same as what we saw in Diverging bars, except that only point are used. Below example uses the same data prepared in the <a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#Diverging%20Bars">diverging bars example</a>.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())

<span class="co"># Plot</span>
<span class="kw">ggplot</span>(mtcars, <span class="kw">aes</span>(<span class="dt">x=</span><span class="st">`</span><span class="dt">car name</span><span class="st">`</span>, <span class="dt">y=</span>mpg_z, <span class="dt">label=</span>mpg_z)) + 
  <span class="kw">geom_point</span>(<span class="dt">stat=</span><span class="st">'identity'</span>, <span class="kw">aes</span>(<span class="dt">col=</span>mpg_type), <span class="dt">size=</span><span class="dv">6</span>)  +
  <span class="kw">scale_color_manual</span>(<span class="dt">name=</span><span class="st">"Mileage"</span>, 
                     <span class="dt">labels =</span> <span class="kw">c</span>(<span class="st">"Above Average"</span>, <span class="st">"Below Average"</span>), 
                     <span class="dt">values =</span> <span class="kw">c</span>(<span class="st">"above"</span>=<span class="st">"#00ba38"</span>, <span class="st">"below"</span>=<span class="st">"#f8766d"</span>)) + 
  <span class="kw">geom_text</span>(<span class="dt">color=</span><span class="st">"white"</span>, <span class="dt">size=</span><span class="dv">2</span>) +
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Diverging Dot Plot"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Normalized mileage from 'mtcars': Dotplot"</span>) + 
  <span class="kw">ylim</span>(-<span class="fl">2.5</span>, <span class="fl">2.5</span>) +
  <span class="kw">coord_flip</span>()</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_12.png" alt="ggplot2 Dotplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Area Chart"></a>Area Chart</h3>
Area charts are typically used to visualize how a particular metric (such as % returns from a stock) performed compared to a certain baseline. Other types of %returns or %change data are also commonly used. The <code>geom_area()</code> implements this.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(quantmod)
<span class="kw">data</span>(<span class="st">"economics"</span>, <span class="dt">package =</span> <span class="st">"ggplot2"</span>)

<span class="co"># Compute % Returns</span>
economics$returns_perc &lt;- <span class="kw">c</span>(<span class="dv">0</span>, <span class="kw">diff</span>(economics$psavert)/economics$psavert[-<span class="kw">length</span>(economics$psavert)])

<span class="co"># Create break points and labels for axis ticks</span>
brks &lt;- economics$date[<span class="kw">seq</span>(<span class="dv">1</span>, <span class="kw">length</span>(economics$date), <span class="dv">12</span>)]
lbls &lt;- lubridate::<span class="kw">year</span>(economics$date[<span class="kw">seq</span>(<span class="dv">1</span>, <span class="kw">length</span>(economics$date), <span class="dv">12</span>)])

<span class="co"># Plot</span>
<span class="kw">ggplot</span>(economics[<span class="dv">1</span>:<span class="dv">100</span>, ], <span class="kw">aes</span>(date, returns_perc)) + 
  <span class="kw">geom_area</span>() + 
  <span class="kw">scale_x_date</span>(<span class="dt">breaks=</span>brks, <span class="dt">labels=</span>lbls) + 
  <span class="kw">theme</span>(<span class="dt">axis.text.x =</span> <span class="kw">element_text</span>(<span class="dt">angle=</span><span class="dv">90</span>)) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Area Chart"</span>, 
       <span class="dt">subtitle =</span> <span class="st">"Perc Returns for Personal Savings"</span>, 
       <span class="dt">y=</span><span class="st">"% Returns for Personal savings"</span>, 
       <span class="dt">caption=</span><span class="st">"Source: economics"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_13.png" alt="ggplot2 Area Chart" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h2 id="3. Ranking">3. Ranking</h2>
Used to compare the position or performance of multiple items with respect to each other. Actual values matters somewhat less than the ranking.
<h3><a name="Ordered Bar Chart"></a>Ordered Bar Chart</h3>
Ordered Bar Chart is a Bar Chart that is ordered by the Y axis variable. Just sorting the dataframe by the variable of interest isn’t enough to order the bar chart. In order for the bar chart to retain the order of the rows, the X axis variable (i.e. the categories) has to be converted into a factor.

Let’s plot the mean city mileage for each manufacturer from <code>mpg</code> dataset. First, aggregate the data and sort it before you draw the plot. Finally, the X variable is converted to a factor.

Let’s see how that is done.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># Prepare data: group mean city mileage by manufacturer.</span>
cty_mpg &lt;- <span class="kw">aggregate</span>(mpg$cty, <span class="dt">by=</span><span class="kw">list</span>(mpg$manufacturer), <span class="dt">FUN=</span>mean)  <span class="co"># aggregate</span>
<span class="kw">colnames</span>(cty_mpg) &lt;- <span class="kw">c</span>(<span class="st">"make"</span>, <span class="st">"mileage"</span>)  <span class="co"># change column names</span>
cty_mpg &lt;- cty_mpg[<span class="kw">order</span>(cty_mpg$mileage), ]  <span class="co"># sort</span>
cty_mpg$make &lt;- <span class="kw">factor</span>(cty_mpg$make, <span class="dt">levels =</span> cty_mpg$make)  <span class="co"># to retain the order in plot.</span>
<span class="kw">head</span>(cty_mpg, <span class="dv">4</span>)
<span class="co">#&gt;          make  mileage</span>
<span class="co">#&gt; 9     lincoln 11.33333</span>
<span class="co">#&gt; 8  land rover 11.50000</span>
<span class="co">#&gt; 3       dodge 13.13514</span>
<span class="co">#&gt; 10    mercury 13.25000</span></code></pre>
</div>
The X variable is now a <code>factor</code>, let’s plot.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())

<span class="co"># Draw plot</span>
<span class="kw">ggplot</span>(cty_mpg, <span class="kw">aes</span>(<span class="dt">x=</span>make, <span class="dt">y=</span>mileage)) + 
  <span class="kw">geom_bar</span>(<span class="dt">stat=</span><span class="st">"identity"</span>, <span class="dt">width=</span>.<span class="dv">5</span>, <span class="dt">fill=</span><span class="st">"tomato3"</span>) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Ordered Bar Chart"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Make Vs Avg. Mileage"</span>, 
       <span class="dt">caption=</span><span class="st">"source: mpg"</span>) + 
  <span class="kw">theme</span>(<span class="dt">axis.text.x =</span> <span class="kw">element_text</span>(<span class="dt">angle=</span><span class="dv">65</span>, <span class="dt">vjust=</span><span class="fl">0.6</span>))</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_14.png" alt="ggplot2 Ordered Barchart" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Lollipop Chart"></a>Lollipop Chart</h3>
Lollipop charts conveys the same information as in bar charts. By reducing the thick bars into thin lines, it reduces the clutter and lays more emphasis on the value. It looks nice and modern.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())

<span class="co"># Plot</span>
<span class="kw">ggplot</span>(cty_mpg, <span class="kw">aes</span>(<span class="dt">x=</span>make, <span class="dt">y=</span>mileage)) + 
  <span class="kw">geom_point</span>(<span class="dt">size=</span><span class="dv">3</span>) + 
  <span class="kw">geom_segment</span>(<span class="kw">aes</span>(<span class="dt">x=</span>make, 
                   <span class="dt">xend=</span>make, 
                   <span class="dt">y=</span><span class="dv">0</span>, 
                   <span class="dt">yend=</span>mileage)) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Lollipop Chart"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Make Vs Avg. Mileage"</span>, 
       <span class="dt">caption=</span><span class="st">"source: mpg"</span>) + 
  <span class="kw">theme</span>(<span class="dt">axis.text.x =</span> <span class="kw">element_text</span>(<span class="dt">angle=</span><span class="dv">65</span>, <span class="dt">vjust=</span><span class="fl">0.6</span>))</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_15.png" alt="ggplot2 Lollipop Barchart" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Dot Plot"></a>Dot Plot</h3>
Dot plots are very similar to lollipops, but without the line and is flipped to horizontal position. It emphasizes more on the rank ordering of items with respect to actual values and how far apart are the entities with respect to each other.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(scales)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

<span class="co"># Plot</span>
<span class="kw">ggplot</span>(cty_mpg, <span class="kw">aes</span>(<span class="dt">x=</span>make, <span class="dt">y=</span>mileage)) + 
  <span class="kw">geom_point</span>(<span class="dt">col=</span><span class="st">"tomato2"</span>, <span class="dt">size=</span><span class="dv">3</span>) +   <span class="co"># Draw points</span>
  <span class="kw">geom_segment</span>(<span class="kw">aes</span>(<span class="dt">x=</span>make, 
                   <span class="dt">xend=</span>make, 
                   <span class="dt">y=</span><span class="kw">min</span>(mileage), 
                   <span class="dt">yend=</span><span class="kw">max</span>(mileage)), 
               <span class="dt">linetype=</span><span class="st">"dashed"</span>, 
               <span class="dt">size=</span><span class="fl">0.1</span>) +   <span class="co"># Draw dashed lines</span>
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Dot Plot"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Make Vs Avg. Mileage"</span>, 
       <span class="dt">caption=</span><span class="st">"source: mpg"</span>) +  
  <span class="kw">coord_flip</span>()</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_16.png" alt="ggplot2 Dot Plot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Slope Chart"></a>Slope Chart</h3>
Slope charts are an excellent way of comparing the positional placements between 2 points on time. At the moment, there is no builtin function to construct this. Following code serves as a pointer about how you may approach this.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(scales)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

<span class="co"># prep data</span>
df &lt;- <span class="kw">read.csv</span>(<span class="st">"https://raw.githubusercontent.com/selva86/datasets/master/gdppercap.csv"</span>)
<span class="kw">colnames</span>(df) &lt;- <span class="kw">c</span>(<span class="st">"continent"</span>, <span class="st">"1952"</span>, <span class="st">"1957"</span>)
left_label &lt;- <span class="kw">paste</span>(df$continent, <span class="kw">round</span>(df$<span class="st">`</span><span class="dt">1952</span><span class="st">`</span>),<span class="dt">sep=</span><span class="st">", "</span>)
right_label &lt;- <span class="kw">paste</span>(df$continent, <span class="kw">round</span>(df$<span class="st">`</span><span class="dt">1957</span><span class="st">`</span>),<span class="dt">sep=</span><span class="st">", "</span>)
df$class &lt;- <span class="kw">ifelse</span>((df$<span class="st">`</span><span class="dt">1957</span><span class="st">`</span> - df$<span class="st">`</span><span class="dt">1952</span><span class="st">`</span>) &lt; <span class="dv">0</span>, <span class="st">"red"</span>, <span class="st">"green"</span>)

<span class="co"># Plot</span>
p &lt;- <span class="kw">ggplot</span>(df) + <span class="kw">geom_segment</span>(<span class="kw">aes</span>(<span class="dt">x=</span><span class="dv">1</span>, <span class="dt">xend=</span><span class="dv">2</span>, <span class="dt">y=</span><span class="st">`</span><span class="dt">1952</span><span class="st">`</span>, <span class="dt">yend=</span><span class="st">`</span><span class="dt">1957</span><span class="st">`</span>, <span class="dt">col=</span>class), <span class="dt">size=</span>.<span class="dv">75</span>, <span class="dt">show.legend=</span>F) + 
                  <span class="kw">geom_vline</span>(<span class="dt">xintercept=</span><span class="dv">1</span>, <span class="dt">linetype=</span><span class="st">"dashed"</span>, <span class="dt">size=</span>.<span class="dv">1</span>) + 
                  <span class="kw">geom_vline</span>(<span class="dt">xintercept=</span><span class="dv">2</span>, <span class="dt">linetype=</span><span class="st">"dashed"</span>, <span class="dt">size=</span>.<span class="dv">1</span>) +
                  <span class="kw">scale_color_manual</span>(<span class="dt">labels =</span> <span class="kw">c</span>(<span class="st">"Up"</span>, <span class="st">"Down"</span>), 
                                     <span class="dt">values =</span> <span class="kw">c</span>(<span class="st">"green"</span>=<span class="st">"#00ba38"</span>, <span class="st">"red"</span>=<span class="st">"#f8766d"</span>)) +  <span class="co"># color of lines</span>
                  <span class="kw">labs</span>(<span class="dt">x=</span><span class="st">""</span>, <span class="dt">y=</span><span class="st">"Mean GdpPerCap"</span>) +  <span class="co"># Axis labels</span>
                  <span class="kw">xlim</span>(.<span class="dv">5</span>, <span class="fl">2.5</span>) + <span class="kw">ylim</span>(<span class="dv">0</span>,(<span class="fl">1.1</span>*(<span class="kw">max</span>(df$<span class="st">`</span><span class="dt">1952</span><span class="st">`</span>, df$<span class="st">`</span><span class="dt">1957</span><span class="st">`</span>))))  <span class="co"># X and Y axis limits</span>

<span class="co"># Add texts</span>
p &lt;- p + <span class="kw">geom_text</span>(<span class="dt">label=</span>left_label, <span class="dt">y=</span>df$<span class="st">`</span><span class="dt">1952</span><span class="st">`</span>, <span class="dt">x=</span><span class="kw">rep</span>(<span class="dv">1</span>, <span class="kw">NROW</span>(df)), <span class="dt">hjust=</span><span class="fl">1.1</span>, <span class="dt">size=</span><span class="fl">3.5</span>)
p &lt;- p + <span class="kw">geom_text</span>(<span class="dt">label=</span>right_label, <span class="dt">y=</span>df$<span class="st">`</span><span class="dt">1957</span><span class="st">`</span>, <span class="dt">x=</span><span class="kw">rep</span>(<span class="dv">2</span>, <span class="kw">NROW</span>(df)), <span class="dt">hjust=</span>-<span class="fl">0.1</span>, <span class="dt">size=</span><span class="fl">3.5</span>)
p &lt;- p + <span class="kw">geom_text</span>(<span class="dt">label=</span><span class="st">"Time 1"</span>, <span class="dt">x=</span><span class="dv">1</span>, <span class="dt">y=</span><span class="fl">1.1</span>*(<span class="kw">max</span>(df$<span class="st">`</span><span class="dt">1952</span><span class="st">`</span>, df$<span class="st">`</span><span class="dt">1957</span><span class="st">`</span>)), <span class="dt">hjust=</span><span class="fl">1.2</span>, <span class="dt">size=</span><span class="dv">5</span>)  <span class="co"># title</span>
p &lt;- p + <span class="kw">geom_text</span>(<span class="dt">label=</span><span class="st">"Time 2"</span>, <span class="dt">x=</span><span class="dv">2</span>, <span class="dt">y=</span><span class="fl">1.1</span>*(<span class="kw">max</span>(df$<span class="st">`</span><span class="dt">1952</span><span class="st">`</span>, df$<span class="st">`</span><span class="dt">1957</span><span class="st">`</span>)), <span class="dt">hjust=</span>-<span class="fl">0.1</span>, <span class="dt">size=</span><span class="dv">5</span>)  <span class="co"># title</span>

<span class="co"># Minify theme</span>
p + <span class="kw">theme</span>(<span class="dt">panel.background =</span> <span class="kw">element_blank</span>(), 
           <span class="dt">panel.grid =</span> <span class="kw">element_blank</span>(),
           <span class="dt">axis.ticks =</span> <span class="kw">element_blank</span>(),
           <span class="dt">axis.text.x =</span> <span class="kw">element_blank</span>(),
           <span class="dt">panel.border =</span> <span class="kw">element_blank</span>(),
           <span class="dt">plot.margin =</span> <span class="kw">unit</span>(<span class="kw">c</span>(<span class="dv">1</span>,<span class="dv">2</span>,<span class="dv">1</span>,<span class="dv">2</span>), <span class="st">"cm"</span>))</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_17.png" alt="ggplot2 Slope Chart" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Dumbbell Plot"></a>Dumbbell Plot</h3>
Dumbbell charts are a great tool if you wish to: 1. Visualize relative positions (like growth and decline) between two points in time. 2. Compare distance between two categories.

In order to get the correct ordering of the dumbbells, the Y variable should be a factor and the levels of the factor variable should be in the same order as it should appear in the plot.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># devtools::install_github("hrbrmstr/ggalt")</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(ggalt)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

health &lt;- <span class="kw">read.csv</span>(<span class="st">"https://raw.githubusercontent.com/selva86/datasets/master/health.csv"</span>)
health$Area &lt;- <span class="kw">factor</span>(health$Area, <span class="dt">levels=</span><span class="kw">as.character</span>(health$Area))  <span class="co"># for right ordering of the dumbells</span>

<span class="co"># health$Area &lt;- factor(health$Area)</span>
gg &lt;- <span class="kw">ggplot</span>(health, <span class="kw">aes</span>(<span class="dt">x=</span>pct_2013, <span class="dt">xend=</span>pct_2014, <span class="dt">y=</span>Area, <span class="dt">group=</span>Area)) + 
        <span class="kw">geom_dumbbell</span>(<span class="dt">color=</span><span class="st">"#a3c4dc"</span>, 
                      <span class="dt">size=</span><span class="fl">0.75</span>, 
                      <span class="dt">point.colour.l=</span><span class="st">"#0e668b"</span>) + 
        <span class="kw">scale_x_continuous</span>(<span class="dt">label=</span>percent) + 
        <span class="kw">labs</span>(<span class="dt">x=</span><span class="ot">NULL</span>, 
             <span class="dt">y=</span><span class="ot">NULL</span>, 
             <span class="dt">title=</span><span class="st">"Dumbbell Chart"</span>, 
             <span class="dt">subtitle=</span><span class="st">"Pct Change: 2013 vs 2014"</span>, 
             <span class="dt">caption=</span><span class="st">"Source: https://github.com/hrbrmstr/ggalt"</span>) +
        <span class="kw">theme</span>(<span class="dt">plot.title =</span> <span class="kw">element_text</span>(<span class="dt">hjust=</span><span class="fl">0.5</span>, <span class="dt">face=</span><span class="st">"bold"</span>),
              <span class="dt">plot.background=</span><span class="kw">element_rect</span>(<span class="dt">fill=</span><span class="st">"#f7f7f7"</span>),
              <span class="dt">panel.background=</span><span class="kw">element_rect</span>(<span class="dt">fill=</span><span class="st">"#f7f7f7"</span>),
              <span class="dt">panel.grid.minor=</span><span class="kw">element_blank</span>(),
              <span class="dt">panel.grid.major.y=</span><span class="kw">element_blank</span>(),
              <span class="dt">panel.grid.major.x=</span><span class="kw">element_line</span>(),
              <span class="dt">axis.ticks=</span><span class="kw">element_blank</span>(),
              <span class="dt">legend.position=</span><span class="st">"top"</span>,
              <span class="dt">panel.border=</span><span class="kw">element_blank</span>())
<span class="kw">plot</span>(gg)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_18.png" alt="ggplot2 Dumbbell Chart" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h2 id="4. Distribution">4. Distribution</h2>
When you have lots and lots of data points and want to study where and how the data points are distributed.
<h3><a name="Histogram"></a>Histogram</h3>
By default, if only one variable is supplied, the <code>geom_bar()</code> tries to calculate the count. In order for it to behave like a bar chart, the <code>stat=identity</code> option has to be set and <code>x</code> and <code>y</code> values must be provided.
<h4 id="Histogram on a continuous variable">Histogram on a continuous variable</h4>
Histogram on a continuous variable can be accomplished using either <code>geom_bar()</code> or <code>geom_histogram()</code>. When using <code>geom_histogram()</code>, you can control the number of bars using the <code>bins</code> option. Else, you can set the range covered by each bin using <code>binwidth</code>. The value of <code>binwidth</code> is on the same scale as the continuous variable on which histogram is built. Since, <code>geom_histogram</code> gives facility to control both number of <code>bins</code> as well as <code>binwidth</code>, it is the preferred option to create histogram on continuous variables.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

<span class="co"># Histogram on a Continuous (Numeric) Variable</span>
g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(displ)) + <span class="kw">scale_fill_brewer</span>(<span class="dt">palette =</span> <span class="st">"Spectral"</span>)

g + <span class="kw">geom_histogram</span>(<span class="kw">aes</span>(<span class="dt">fill=</span>class), 
                   <span class="dt">binwidth =</span> .<span class="dv">1</span>, 
                   <span class="dt">col=</span><span class="st">"black"</span>, 
                   <span class="dt">size=</span>.<span class="dv">1</span>) +  <span class="co"># change binwidth</span>
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Histogram with Auto Binning"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Engine Displacement across Vehicle Classes"</span>)  

g + <span class="kw">geom_histogram</span>(<span class="kw">aes</span>(<span class="dt">fill=</span>class), 
                   <span class="dt">bins=</span><span class="dv">5</span>, 
                   <span class="dt">col=</span><span class="st">"black"</span>, 
                   <span class="dt">size=</span>.<span class="dv">1</span>) +   <span class="co"># change number of bins</span>
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Histogram with Fixed Bins"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Engine Displacement across Vehicle Classes"</span>) </code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_19.png" alt="ggplot2 Histogram on Numeric Variable" /> <img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_20.png" alt="ggplot2 Histogram with 5 Bins - Spectral" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h4 id="Histogram on a categorical variable">Histogram on a categorical variable</h4>
Histogram on a categorical variable would result in a frequency chart showing bars for each category. By adjusting <code>width</code>, you can adjust the thickness of the bars.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

<span class="co"># Histogram on a Categorical variable</span>
g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(manufacturer))
g + <span class="kw">geom_bar</span>(<span class="kw">aes</span>(<span class="dt">fill=</span>class), <span class="dt">width =</span> <span class="fl">0.5</span>) + 
  <span class="kw">theme</span>(<span class="dt">axis.text.x =</span> <span class="kw">element_text</span>(<span class="dt">angle=</span><span class="dv">65</span>, <span class="dt">vjust=</span><span class="fl">0.6</span>)) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Histogram on Categorical Variable"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Manufacturer across Vehicle Classes"</span>) </code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_22.png" alt="ggplot2 Histogram on Categorical Variable" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Density Plot"></a>Density plot</h3>
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

<span class="co"># Plot</span>
g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(cty))
g + <span class="kw">geom_density</span>(<span class="kw">aes</span>(<span class="dt">fill=</span><span class="kw">factor</span>(cyl)), <span class="dt">alpha=</span><span class="fl">0.8</span>) + 
    <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Density plot"</span>, 
         <span class="dt">subtitle=</span><span class="st">"City Mileage Grouped by Number of cylinders"</span>,
         <span class="dt">caption=</span><span class="st">"Source: mpg"</span>,
         <span class="dt">x=</span><span class="st">"City Mileage"</span>,
         <span class="dt">fill=</span><span class="st">"# Cylinders"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_23.png" alt="ggplot2 Density Plot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Box Plot"></a>Box Plot</h3>
Box plot is an excellent tool to study the distribution. It can also show the distributions within multiple groups, along with the median, range and outliers if any.

The dark line inside the box represents the median. The top of box is 75%ile and bottom of box is 25%ile. The end points of the lines (aka whiskers) is at a distance of 1.5*IQR, where IQR or Inter Quartile Range is the distance between 25th and 75th percentiles. The points outside the whiskers are marked as dots and are normally considered as extreme points.

Setting <code>varwidth=T</code> adjusts the width of the boxes to be proportional to the number of observation it contains.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

<span class="co"># Plot</span>
g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(class, cty))
g + <span class="kw">geom_boxplot</span>(<span class="dt">varwidth=</span>T, <span class="dt">fill=</span><span class="st">"plum"</span>) + 
    <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Box plot"</span>, 
         <span class="dt">subtitle=</span><span class="st">"City Mileage grouped by Class of vehicle"</span>,
         <span class="dt">caption=</span><span class="st">"Source: mpg"</span>,
         <span class="dt">x=</span><span class="st">"Class of Vehicle"</span>,
         <span class="dt">y=</span><span class="st">"City Mileage"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_24.png" alt="ggplot2 BoxPlot" />
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggthemes)
g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(class, cty))
g + <span class="kw">geom_boxplot</span>(<span class="kw">aes</span>(<span class="dt">fill=</span><span class="kw">factor</span>(cyl))) + 
  <span class="kw">theme</span>(<span class="dt">axis.text.x =</span> <span class="kw">element_text</span>(<span class="dt">angle=</span><span class="dv">65</span>, <span class="dt">vjust=</span><span class="fl">0.6</span>)) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Box plot"</span>, 
       <span class="dt">subtitle=</span><span class="st">"City Mileage grouped by Class of vehicle"</span>,
       <span class="dt">caption=</span><span class="st">"Source: mpg"</span>,
       <span class="dt">x=</span><span class="st">"Class of Vehicle"</span>,
       <span class="dt">y=</span><span class="st">"City Mileage"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_25.png" alt="ggplot2 Grouped BoxPlot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Dot + Box Plot"></a>Dot + Box Plot</h3>
On top of the information provided by a box plot, the dot plot can provide more clear information in the form of summary statistics by each group. The dots are staggered such that each dot represents one observation. So, in below chart, the number of dots for a given manufacturer will match the number of rows of that manufacturer in source data.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())

<span class="co"># plot</span>
g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(manufacturer, cty))
g + <span class="kw">geom_boxplot</span>() + 
  <span class="kw">geom_dotplot</span>(<span class="dt">binaxis=</span><span class="st">'y'</span>, 
               <span class="dt">stackdir=</span><span class="st">'center'</span>, 
               <span class="dt">dotsize =</span> .<span class="dv">5</span>, 
               <span class="dt">fill=</span><span class="st">"red"</span>) +
  <span class="kw">theme</span>(<span class="dt">axis.text.x =</span> <span class="kw">element_text</span>(<span class="dt">angle=</span><span class="dv">65</span>, <span class="dt">vjust=</span><span class="fl">0.6</span>)) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Box plot + Dot plot"</span>, 
       <span class="dt">subtitle=</span><span class="st">"City Mileage vs Class: Each dot represents 1 row in source data"</span>,
       <span class="dt">caption=</span><span class="st">"Source: mpg"</span>,
       <span class="dt">x=</span><span class="st">"Class of Vehicle"</span>,
       <span class="dt">y=</span><span class="st">"City Mileage"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_26.png" alt="ggplot2 Box and DotPlot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Tufte Boxplot"></a>Tufte Boxplot</h3>
Tufte box plot, provided by <code>ggthemes</code> package is inspired by the works of Edward Tufte. Tufte’s Box plot is just a box plot made minimal and visually appealing.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggthemes)
<span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_tufte</span>())  <span class="co"># from ggthemes</span>

<span class="co"># plot</span>
g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(manufacturer, cty))
g + <span class="kw">geom_tufteboxplot</span>() + 
      <span class="kw">theme</span>(<span class="dt">axis.text.x =</span> <span class="kw">element_text</span>(<span class="dt">angle=</span><span class="dv">65</span>, <span class="dt">vjust=</span><span class="fl">0.6</span>)) + 
      <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Tufte Styled Boxplot"</span>, 
           <span class="dt">subtitle=</span><span class="st">"City Mileage grouped by Class of vehicle"</span>,
           <span class="dt">caption=</span><span class="st">"Source: mpg"</span>,
           <span class="dt">x=</span><span class="st">"Class of Vehicle"</span>,
           <span class="dt">y=</span><span class="st">"City Mileage"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_27.png" alt="ggplot2 Tufte Boxplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Violin Plot"></a>Violin Plot</h3>
A violin plot is similar to box plot but shows the density within groups. Not much info provided as in boxplots. It can be drawn using <code>geom_violin()</code>.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())

<span class="co"># plot</span>
g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(class, cty))
g + <span class="kw">geom_violin</span>() + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Violin plot"</span>, 
       <span class="dt">subtitle=</span><span class="st">"City Mileage vs Class of vehicle"</span>,
       <span class="dt">caption=</span><span class="st">"Source: mpg"</span>,
       <span class="dt">x=</span><span class="st">"Class of Vehicle"</span>,
       <span class="dt">y=</span><span class="st">"City Mileage"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_28.png" alt="ggplot2 Violin Plot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Population Pyramid"></a>Population Pyramid</h3>
Population pyramids offer a unique way of visualizing how much population or what percentage of population fall under a certain category. The below pyramid is an excellent example of how many users are retained at each stage of a email marketing campaign funnel.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(ggthemes)
<span class="kw">options</span>(<span class="dt">scipen =</span> <span class="dv">999</span>)  <span class="co"># turns of scientific notations like 1e+40</span>

<span class="co"># Read data</span>
email_campaign_funnel &lt;- <span class="kw">read.csv</span>(<span class="st">"https://raw.githubusercontent.com/selva86/datasets/master/email_campaign_funnel.csv"</span>)

<span class="co"># X Axis Breaks and Labels </span>
brks &lt;- <span class="kw">seq</span>(-<span class="dv">15000000</span>, <span class="dv">15000000</span>, <span class="dv">5000000</span>)
lbls = <span class="kw">paste0</span>(<span class="kw">as.character</span>(<span class="kw">c</span>(<span class="kw">seq</span>(<span class="dv">15</span>, <span class="dv">0</span>, -<span class="dv">5</span>), <span class="kw">seq</span>(<span class="dv">5</span>, <span class="dv">15</span>, <span class="dv">5</span>))), <span class="st">"m"</span>)

<span class="co"># Plot</span>
<span class="kw">ggplot</span>(email_campaign_funnel, <span class="kw">aes</span>(<span class="dt">x =</span> Stage, <span class="dt">y =</span> Users, <span class="dt">fill =</span> Gender)) +   <span class="co"># Fill column</span>
                              <span class="kw">geom_bar</span>(<span class="dt">stat =</span> <span class="st">"identity"</span>, <span class="dt">width =</span> .<span class="dv">6</span>) +   <span class="co"># draw the bars</span>
                              <span class="kw">scale_y_continuous</span>(<span class="dt">breaks =</span> brks,   <span class="co"># Breaks</span>
                                                 <span class="dt">labels =</span> lbls) + <span class="co"># Labels</span>
                              <span class="kw">coord_flip</span>() +  <span class="co"># Flip axes</span>
                              <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Email Campaign Funnel"</span>) +
                              <span class="kw">theme_tufte</span>() +  <span class="co"># Tufte theme from ggfortify</span>
                              <span class="kw">theme</span>(<span class="dt">plot.title =</span> <span class="kw">element_text</span>(<span class="dt">hjust =</span> .<span class="dv">5</span>), 
                                    <span class="dt">axis.ticks =</span> <span class="kw">element_blank</span>()) +   <span class="co"># Centre plot title</span>
                              <span class="kw">scale_fill_brewer</span>(<span class="dt">palette =</span> <span class="st">"Dark2"</span>)  <span class="co"># Color palette</span></code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_29.png" alt="Population Pyramid With Ggplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h2 id="5. Composition">5. Composition</h2>
<h3><a name="Waffle Chart"></a>Waffle Chart</h3>
Waffle charts is a nice way of showing the categorical composition of the total population. Though there is no direct function, it can be articulated by smartly maneuvering the ggplot2 using <code>geom_tile()</code>function. The below template should help you create your own waffle.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r">var &lt;- mpg$class  <span class="co"># the categorical data </span>

## Prep data (nothing to change here)
nrows &lt;- <span class="dv">10</span>
df &lt;- <span class="kw">expand.grid</span>(<span class="dt">y =</span> <span class="dv">1</span>:nrows, <span class="dt">x =</span> <span class="dv">1</span>:nrows)
categ_table &lt;- <span class="kw">round</span>(<span class="kw">table</span>(var) * ((nrows*nrows)/(<span class="kw">length</span>(var))))
categ_table
<span class="co">#&gt;   2seater    compact    midsize    minivan     pickup subcompact        suv </span>
<span class="co">#&gt;         2         20         18          5         14         15         26 </span>

df$category &lt;- <span class="kw">factor</span>(<span class="kw">rep</span>(<span class="kw">names</span>(categ_table), categ_table))  
<span class="co"># NOTE: if sum(categ_table) is not 100 (i.e. nrows^2), it will need adjustment to make the sum to 100.</span>

## Plot
<span class="kw">ggplot</span>(df, <span class="kw">aes</span>(<span class="dt">x =</span> x, <span class="dt">y =</span> y, <span class="dt">fill =</span> category)) + 
        <span class="kw">geom_tile</span>(<span class="dt">color =</span> <span class="st">"black"</span>, <span class="dt">size =</span> <span class="fl">0.5</span>) +
        <span class="kw">scale_x_continuous</span>(<span class="dt">expand =</span> <span class="kw">c</span>(<span class="dv">0</span>, <span class="dv">0</span>)) +
        <span class="kw">scale_y_continuous</span>(<span class="dt">expand =</span> <span class="kw">c</span>(<span class="dv">0</span>, <span class="dv">0</span>), <span class="dt">trans =</span> <span class="st">'reverse'</span>) +
        <span class="kw">scale_fill_brewer</span>(<span class="dt">palette =</span> <span class="st">"Set3"</span>) +
        <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Waffle Chart"</span>, <span class="dt">subtitle=</span><span class="st">"'Class' of vehicles"</span>,
             <span class="dt">caption=</span><span class="st">"Source: mpg"</span>) + 
        <span class="kw">theme</span>(<span class="dt">panel.border =</span> <span class="kw">element_rect</span>(<span class="dt">size =</span> <span class="dv">2</span>),
              <span class="dt">plot.title =</span> <span class="kw">element_text</span>(<span class="dt">size =</span> <span class="kw">rel</span>(<span class="fl">1.2</span>)),
              <span class="dt">axis.text =</span> <span class="kw">element_blank</span>(),
              <span class="dt">axis.title =</span> <span class="kw">element_blank</span>(),
              <span class="dt">axis.ticks =</span> <span class="kw">element_blank</span>(),
              <span class="dt">legend.title =</span> <span class="kw">element_blank</span>(),
              <span class="dt">legend.position =</span> <span class="st">"right"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_30.png" alt="Waffle Chart With Ggplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Pie Chart"></a>Pie Chart</h3>
Pie chart, a classic way of showing the compositions is equivalent to the waffle chart in terms of the information conveyed. But is a slightly tricky to implement in ggplot2 using the <code>coord_polar()</code>.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

<span class="co"># Source: Frequency table</span>
df &lt;- <span class="kw">as.data.frame</span>(<span class="kw">table</span>(mpg$class))
<span class="kw">colnames</span>(df) &lt;- <span class="kw">c</span>(<span class="st">"class"</span>, <span class="st">"freq"</span>)
pie &lt;- <span class="kw">ggplot</span>(df, <span class="kw">aes</span>(<span class="dt">x =</span> <span class="st">""</span>, <span class="dt">y=</span>freq, <span class="dt">fill =</span> <span class="kw">factor</span>(class))) + 
  <span class="kw">geom_bar</span>(<span class="dt">width =</span> <span class="dv">1</span>, <span class="dt">stat =</span> <span class="st">"identity"</span>) +
  <span class="kw">theme</span>(<span class="dt">axis.line =</span> <span class="kw">element_blank</span>(), 
        <span class="dt">plot.title =</span> <span class="kw">element_text</span>(<span class="dt">hjust=</span><span class="fl">0.5</span>)) + 
  <span class="kw">labs</span>(<span class="dt">fill=</span><span class="st">"class"</span>, 
       <span class="dt">x=</span><span class="ot">NULL</span>, 
       <span class="dt">y=</span><span class="ot">NULL</span>, 
       <span class="dt">title=</span><span class="st">"Pie Chart of class"</span>, 
       <span class="dt">caption=</span><span class="st">"Source: mpg"</span>)

pie + <span class="kw">coord_polar</span>(<span class="dt">theta =</span> <span class="st">"y"</span>, <span class="dt">start=</span><span class="dv">0</span>)

<span class="co"># Source: Categorical variable.</span>
<span class="co"># mpg$class</span>
pie &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(<span class="dt">x =</span> <span class="st">""</span>, <span class="dt">fill =</span> <span class="kw">factor</span>(class))) + 
  <span class="kw">geom_bar</span>(<span class="dt">width =</span> <span class="dv">1</span>) +
  <span class="kw">theme</span>(<span class="dt">axis.line =</span> <span class="kw">element_blank</span>(), 
        <span class="dt">plot.title =</span> <span class="kw">element_text</span>(<span class="dt">hjust=</span><span class="fl">0.5</span>)) + 
  <span class="kw">labs</span>(<span class="dt">fill=</span><span class="st">"class"</span>, 
       <span class="dt">x=</span><span class="ot">NULL</span>, 
       <span class="dt">y=</span><span class="ot">NULL</span>, 
       <span class="dt">title=</span><span class="st">"Pie Chart of class"</span>, 
       <span class="dt">caption=</span><span class="st">"Source: mpg"</span>)
  
pie + <span class="kw">coord_polar</span>(<span class="dt">theta =</span> <span class="st">"y"</span>, <span class="dt">start=</span><span class="dv">0</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_31.png" alt="Pie Chart With Ggplot" />
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># http://www.r-graph-gallery.com/128-ring-or-donut-plot/</span></code></pre>
</div>
<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Treemap"></a>Treemap</h3>
Treemap is a nice way of displaying hierarchical data by using nested rectangles. The <code>treemapify</code>package provides the necessary functions to convert the data in desired format (<code>treemapify</code>) as well as draw the actual plot (<code>ggplotify</code>).

In order to create a treemap, the data must be converted to desired format using <code>treemapify()</code>. The important requirement is, your data must have one variable each that describes the <code>area</code> of the tiles, variable for <code>fill</code> color, variable that has the tile’s <code>label</code> and finally the parent <code>group</code>.

Once the data formatting is done, just call <code>ggplotify()</code> on the treemapified data.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2) 
<span class="kw">library</span>(treemapify)
proglangs &lt;- <span class="kw">read.csv</span>(<span class="st">"https://raw.githubusercontent.com/selva86/datasets/master/proglanguages.csv"</span>)

<span class="co"># plot</span>
treeMapCoordinates &lt;- <span class="kw">treemapify</span>(proglangs,
                                 <span class="dt">area =</span> <span class="st">"value"</span>,
                                 <span class="dt">fill =</span> <span class="st">"parent"</span>,
                                 <span class="dt">label =</span> <span class="st">"id"</span>,
                                 <span class="dt">group =</span> <span class="st">"parent"</span>)

treeMapPlot &lt;- <span class="kw">ggplotify</span>(treeMapCoordinates) + 
                  <span class="kw">scale_x_continuous</span>(<span class="dt">expand =</span> <span class="kw">c</span>(<span class="dv">0</span>, <span class="dv">0</span>)) +
                  <span class="kw">scale_y_continuous</span>(<span class="dt">expand =</span> <span class="kw">c</span>(<span class="dv">0</span>, <span class="dv">0</span>)) +
                  <span class="kw">scale_fill_brewer</span>(<span class="dt">palette =</span> <span class="st">"Dark2"</span>)

<span class="kw">print</span>(treeMapPlot)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_32.png" alt="Treemap With Ggplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Bar Chart"></a>Bar Chart</h3>
By default, <code>geom_bar()</code> has the <code>stat</code> set to <code>count</code>. That means, when you provide just a continuous X variable (and no Y variable), it tries to make a histogram out of the data.

In order to make a bar chart create bars instead of histogram, you need to do two things.
<ol>
 	<li>Set <code>stat=identity</code></li>
 	<li>Provide both <code>x</code> and <code>y</code> inside <code>aes()</code> where, <code>x</code> is either <code>character</code> or <code>factor</code> and <code>y</code> is numeric.</li>
</ol>
A bar chart can be drawn from a categorical column variable or from a separate frequency table. By adjusting <code>width</code>, you can adjust the thickness of the bars. If your data source is a frequency table, that is, if you don’t want ggplot to compute the counts, you need to set the <code>stat=identity</code> inside the <code>geom_bar()</code>.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># prep frequency table</span>
freqtable &lt;- <span class="kw">table</span>(mpg$manufacturer)
df &lt;- <span class="kw">as.data.frame.table</span>(freqtable)
<span class="kw">head</span>(df)
<span class="co">#&gt;          Var1 Freq</span>
<span class="co">#&gt; 1        audi   18</span>
<span class="co">#&gt; 2   chevrolet   19</span>
<span class="co">#&gt; 3       dodge   37</span>
<span class="co">#&gt; 4        ford   25</span>
<span class="co">#&gt; 5       honda    9</span>
<span class="co">#&gt; 6     hyundai   14</span></code></pre>
</div>
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># plot</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

<span class="co"># Plot</span>
g &lt;- <span class="kw">ggplot</span>(df, <span class="kw">aes</span>(Var1, Freq))
g + <span class="kw">geom_bar</span>(<span class="dt">stat=</span><span class="st">"identity"</span>, <span class="dt">width =</span> <span class="fl">0.5</span>, <span class="dt">fill=</span><span class="st">"tomato2"</span>) + 
      <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Bar Chart"</span>, 
           <span class="dt">subtitle=</span><span class="st">"Manufacturer of vehicles"</span>, 
           <span class="dt">caption=</span><span class="st">"Source: Frequency of Manufacturers from 'mpg' dataset"</span>) +
      <span class="kw">theme</span>(<span class="dt">axis.text.x =</span> <span class="kw">element_text</span>(<span class="dt">angle=</span><span class="dv">65</span>, <span class="dt">vjust=</span><span class="fl">0.6</span>))</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_33.png" alt="Bar Chart With Ggplot" />

It can be computed directly from a column variable as well. In this case, only X is provided and <code>stat=identity</code> is <em>not</em> set.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># From on a categorical column variable</span>
g &lt;- <span class="kw">ggplot</span>(mpg, <span class="kw">aes</span>(manufacturer))
g + <span class="kw">geom_bar</span>(<span class="kw">aes</span>(<span class="dt">fill=</span>class), <span class="dt">width =</span> <span class="fl">0.5</span>) + 
  <span class="kw">theme</span>(<span class="dt">axis.text.x =</span> <span class="kw">element_text</span>(<span class="dt">angle=</span><span class="dv">65</span>, <span class="dt">vjust=</span><span class="fl">0.6</span>)) +
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Categorywise Bar Chart"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Manufacturer of vehicles"</span>, 
       <span class="dt">caption=</span><span class="st">"Source: Manufacturers from 'mpg' dataset"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_34.png" alt="Bar Chart With Multiple Categories in Ggplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h2 id="6. Change">6. Change</h2>
<h3><a name="Time Series Plot From a Time Series Object"></a>Time Series Plot From a Time Series Object (<code>ts</code>)</h3>
The <code>ggfortify</code> package allows autoplot to automatically plot directly from a time series object (<code>ts</code>).
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r">## From Timeseries object (ts)
<span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(ggfortify)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

<span class="co"># Plot </span>
<span class="kw">autoplot</span>(AirPassengers) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"AirPassengers"</span>) + 
  <span class="kw">theme</span>(<span class="dt">plot.title =</span> <span class="kw">element_text</span>(<span class="dt">hjust=</span><span class="fl">0.5</span>))</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_35.png" alt="Time series in ggplot with ts object" />
<h3><a name="Time Series Plot From a Data Frame"></a>Time Series Plot From a Data Frame</h3>
Using <code>geom_line()</code>, a time series (or line chart) can be drawn from a <code>data.frame</code> as well. The X axis breaks are generated by default. In below example, the breaks are formed once every 10 years.
<h4 id="Default X Axis Labels">Default X Axis Labels</h4>
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

<span class="co"># Allow Default X Axis Labels</span>
<span class="kw">ggplot</span>(economics, <span class="kw">aes</span>(<span class="dt">x=</span>date)) + 
  <span class="kw">geom_line</span>(<span class="kw">aes</span>(<span class="dt">y=</span>returns_perc)) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Time Series Chart"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Returns Percentage from 'Economics' Dataset"</span>, 
       <span class="dt">caption=</span><span class="st">"Source: Economics"</span>, 
       <span class="dt">y=</span><span class="st">"Returns %"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_36.png" alt="Time series in ggplot from Dataframe" />
<h3><a name="Time Series Plot For a Monthly Time Series"></a>Time Series Plot For a <em>Monthly</em> Time Series</h3>
If you want to set your own time intervals (breaks) in X axis, you need to set the breaks and labels using <code>scale_x_date()</code>.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(lubridate)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())

economics_m &lt;- economics[<span class="dv">1</span>:<span class="dv">24</span>, ]

<span class="co"># labels and breaks for X axis text</span>
lbls &lt;- <span class="kw">paste0</span>(month.abb[<span class="kw">month</span>(economics_m$date)], <span class="st">" "</span>, lubridate::<span class="kw">year</span>(economics_m$date))
brks &lt;- economics_m$date

<span class="co"># plot</span>
<span class="kw">ggplot</span>(economics_m, <span class="kw">aes</span>(<span class="dt">x=</span>date)) + 
  <span class="kw">geom_line</span>(<span class="kw">aes</span>(<span class="dt">y=</span>returns_perc)) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Monthly Time Series"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Returns Percentage from Economics Dataset"</span>, 
       <span class="dt">caption=</span><span class="st">"Source: Economics"</span>, 
       <span class="dt">y=</span><span class="st">"Returns %"</span>) +  <span class="co"># title and caption</span>
  <span class="kw">scale_x_date</span>(<span class="dt">labels =</span> lbls, 
               <span class="dt">breaks =</span> brks) +  <span class="co"># change to monthly ticks and labels</span>
  <span class="kw">theme</span>(<span class="dt">axis.text.x =</span> <span class="kw">element_text</span>(<span class="dt">angle =</span> <span class="dv">90</span>, <span class="dt">vjust=</span><span class="fl">0.5</span>),  <span class="co"># rotate x axis text</span>
        <span class="dt">panel.grid.minor =</span> <span class="kw">element_blank</span>())  <span class="co"># turn off minor grid</span></code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_37.png" alt="Monthly Time series in ggplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Time Series Plot For a Yearly Time Series"></a>Time Series Plot For a <em>Yearly</em> Time Series</h3>
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(lubridate)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())

economics_y &lt;- economics[<span class="dv">1</span>:<span class="dv">90</span>, ]

<span class="co"># labels and breaks for X axis text</span>
brks &lt;- economics_y$date[<span class="kw">seq</span>(<span class="dv">1</span>, <span class="kw">length</span>(economics_y$date), <span class="dv">12</span>)]
lbls &lt;- lubridate::<span class="kw">year</span>(brks)

<span class="co"># plot</span>
<span class="kw">ggplot</span>(economics_y, <span class="kw">aes</span>(<span class="dt">x=</span>date)) + 
  <span class="kw">geom_line</span>(<span class="kw">aes</span>(<span class="dt">y=</span>returns_perc)) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Yearly Time Series"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Returns Percentage from Economics Dataset"</span>, 
       <span class="dt">caption=</span><span class="st">"Source: Economics"</span>, 
       <span class="dt">y=</span><span class="st">"Returns %"</span>) +  <span class="co"># title and caption</span>
  <span class="kw">scale_x_date</span>(<span class="dt">labels =</span> lbls, 
               <span class="dt">breaks =</span> brks) +  <span class="co"># change to monthly ticks and labels</span>
  <span class="kw">theme</span>(<span class="dt">axis.text.x =</span> <span class="kw">element_text</span>(<span class="dt">angle =</span> <span class="dv">90</span>, <span class="dt">vjust=</span><span class="fl">0.5</span>),  <span class="co"># rotate x axis text</span>
        <span class="dt">panel.grid.minor =</span> <span class="kw">element_blank</span>())  <span class="co"># turn off minor grid</span></code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_38.png" alt="Yearly Time series in ggplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Time Series Plot From Long Data Format"></a>Time Series Plot From Long Data Format: Multiple Time Series in Same Dataframe Column</h3>
In this example, I construct the ggplot from a long data format. That means, the column names and respective values of all the columns are stacked in just 2 variables (<code>variable</code> and <code>value</code> respectively). If you were to convert this data to wide format, it would look like the <code>economics</code> dataset.

In below example, the <code>geom_line</code> is drawn for <code>value</code> column and the <code>aes(col)</code> is set to <code>variable</code>. This way, with just one call to <code>geom_line</code>, multiple colored lines are drawn, one each for each unique value in <code>variable</code> column. The <code>scale_x_date()</code> changes the X axis breaks and labels, and <code>scale_color_manual</code>changes the color of the lines.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">data</span>(economics_long, <span class="dt">package =</span> <span class="st">"ggplot2"</span>)
<span class="kw">head</span>(economics_long)
<span class="co">#&gt;         date variable value      value01</span>
<span class="co">#&gt;       &lt;date&gt;   &lt;fctr&gt; &lt;dbl&gt;        &lt;dbl&gt;</span>
<span class="co">#&gt; 1 1967-07-01      pce 507.4 0.0000000000</span>
<span class="co">#&gt; 2 1967-08-01      pce 510.5 0.0002660008</span>
<span class="co">#&gt; 3 1967-09-01      pce 516.3 0.0007636797</span>
<span class="co">#&gt; 4 1967-10-01      pce 512.9 0.0004719369</span>
<span class="co">#&gt; 5 1967-11-01      pce 518.1 0.0009181318</span>
<span class="co">#&gt; 6 1967-12-01      pce 525.8 0.0015788435</span></code></pre>
</div>
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(lubridate)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())

df &lt;- economics_long[economics_long$variable %in% <span class="kw">c</span>(<span class="st">"psavert"</span>, <span class="st">"uempmed"</span>), ]
df &lt;- df[lubridate::<span class="kw">year</span>(df$date) %in% <span class="kw">c</span>(<span class="dv">1967</span>:<span class="dv">1981</span>), ]

<span class="co"># labels and breaks for X axis text</span>
brks &lt;- df$date[<span class="kw">seq</span>(<span class="dv">1</span>, <span class="kw">length</span>(df$date), <span class="dv">12</span>)]
lbls &lt;- lubridate::<span class="kw">year</span>(brks)

<span class="co"># plot</span>
<span class="kw">ggplot</span>(df, <span class="kw">aes</span>(<span class="dt">x=</span>date)) + 
  <span class="kw">geom_line</span>(<span class="kw">aes</span>(<span class="dt">y=</span>value, <span class="dt">col=</span>variable)) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Time Series of Returns Percentage"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Drawn from Long Data format"</span>, 
       <span class="dt">caption=</span><span class="st">"Source: Economics"</span>, 
       <span class="dt">y=</span><span class="st">"Returns %"</span>, 
       <span class="dt">color=</span><span class="ot">NULL</span>) +  <span class="co"># title and caption</span>
  <span class="kw">scale_x_date</span>(<span class="dt">labels =</span> lbls, <span class="dt">breaks =</span> brks) +  <span class="co"># change to monthly ticks and labels</span>
  <span class="kw">scale_color_manual</span>(<span class="dt">labels =</span> <span class="kw">c</span>(<span class="st">"psavert"</span>, <span class="st">"uempmed"</span>), 
                     <span class="dt">values =</span> <span class="kw">c</span>(<span class="st">"psavert"</span>=<span class="st">"#00ba38"</span>, <span class="st">"uempmed"</span>=<span class="st">"#f8766d"</span>)) +  <span class="co"># line color</span>
  <span class="kw">theme</span>(<span class="dt">axis.text.x =</span> <span class="kw">element_text</span>(<span class="dt">angle =</span> <span class="dv">90</span>, <span class="dt">vjust=</span><span class="fl">0.5</span>, <span class="dt">size =</span> <span class="dv">8</span>),  <span class="co"># rotate x axis text</span>
        <span class="dt">panel.grid.minor =</span> <span class="kw">element_blank</span>())  <span class="co"># turn off minor grid</span></code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_39.png" alt="Yearly Time series in ggplot from Long Data format" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Time Series Plot From Wide Data Format"></a>Time Series Plot From Wide Data Format: Data in Multiple Columns of Dataframe</h3>
As noted in the <a href="http://r-statistics.co/Complete-Ggplot2-Tutorial-Part2-Customizing-Theme-With-R-Code.html#2.%20Modifying%20Legend">part 2</a> of this tutorial, whenever your plot’s geom (like points, lines, bars, etc) changes the <code>fill</code>, <code>size</code>, <code>col</code>, <code>shape</code> or <code>stroke</code> based on another column, a legend is automatically drawn.

But if you are creating a time series (or even other types of plots) from a wide data format, you have to draw each line manually by calling <code>geom_line()</code> once for every line. So, a legend will not be drawn by default.

However, having a legend would still be nice. This can be done using the <code>scale_aesthetic_manual()</code>format of functions (like, <code>scale_color_manual()</code> if only the color of your lines change). Using this function, you can give a legend title with the <code>name</code> argument, tell what color the legend should take with the <code>values</code> argument and also set the legend labels.

Even though the below plot looks exactly like the previous one, the approach to construct this is different.

You might wonder why I used this function in previous example for long data format as well. Note that, in previous example, it was used to change the color of the line only. Without <code>scale_color_manual()</code>, you would still have got a legend, but the lines would be of a different (default) color. But in current example, without <code>scale_color_manual()</code>, you wouldn’t even have a legend. Try it out!
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(lubridate)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())

df &lt;- economics[, <span class="kw">c</span>(<span class="st">"date"</span>, <span class="st">"psavert"</span>, <span class="st">"uempmed"</span>)]
df &lt;- df[lubridate::<span class="kw">year</span>(df$date) %in% <span class="kw">c</span>(<span class="dv">1967</span>:<span class="dv">1981</span>), ]

<span class="co"># labels and breaks for X axis text</span>
brks &lt;- df$date[<span class="kw">seq</span>(<span class="dv">1</span>, <span class="kw">length</span>(df$date), <span class="dv">12</span>)]
lbls &lt;- lubridate::<span class="kw">year</span>(brks)

<span class="co"># plot</span>
<span class="kw">ggplot</span>(df, <span class="kw">aes</span>(<span class="dt">x=</span>date)) + 
  <span class="kw">geom_line</span>(<span class="kw">aes</span>(<span class="dt">y=</span>psavert, <span class="dt">col=</span><span class="st">"psavert"</span>)) + 
  <span class="kw">geom_line</span>(<span class="kw">aes</span>(<span class="dt">y=</span>uempmed, <span class="dt">col=</span><span class="st">"uempmed"</span>)) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Time Series of Returns Percentage"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Drawn From Wide Data format"</span>, 
       <span class="dt">caption=</span><span class="st">"Source: Economics"</span>, <span class="dt">y=</span><span class="st">"Returns %"</span>) +  <span class="co"># title and caption</span>
  <span class="kw">scale_x_date</span>(<span class="dt">labels =</span> lbls, <span class="dt">breaks =</span> brks) +  <span class="co"># change to monthly ticks and labels</span>
  <span class="kw">scale_color_manual</span>(<span class="dt">name=</span><span class="st">""</span>, 
                     <span class="dt">values =</span> <span class="kw">c</span>(<span class="st">"psavert"</span>=<span class="st">"#00ba38"</span>, <span class="st">"uempmed"</span>=<span class="st">"#f8766d"</span>)) +  <span class="co"># line color</span>
  <span class="kw">theme</span>(<span class="dt">panel.grid.minor =</span> <span class="kw">element_blank</span>())  <span class="co"># turn off minor grid</span></code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_40.png" alt="Time series in ggplot from Wide Data Format" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Stacked Area Chart"></a>Stacked Area Chart</h3>
Stacked area chart is just like a line chart, except that the region below the plot is all colored. This is typically used when:
<ol>
 	<li>You want to describe how a quantity or volume (rather than something like price) changed over time</li>
 	<li>You have many data points. For very few data points, consider plotting a bar chart.</li>
 	<li>You want to show the contribution from individual components.</li>
</ol>
This can be plotted using <code>geom_area</code> which works very much like <code>geom_line</code>. But there is an important point to note. By default, each <code>geom_area()</code> starts from the bottom of Y axis (which is typically 0), but, if you want to show the contribution from individual components, you want the <code>geom_area</code> to be stacked over the top of previous component, rather than the floor of the plot itself. So, you have to add all the bottom layers while setting the <code>y</code> of <code>geom_area</code>.

In below example, I have set it as <code>y=psavert+uempmed</code> for the topmost <code>geom_area()</code>.

However nice the plot looks, the caveat is that, it can easily become complicated and uninterprettable if there are too many components.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(lubridate)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())

df &lt;- economics[, <span class="kw">c</span>(<span class="st">"date"</span>, <span class="st">"psavert"</span>, <span class="st">"uempmed"</span>)]
df &lt;- df[lubridate::<span class="kw">year</span>(df$date) %in% <span class="kw">c</span>(<span class="dv">1967</span>:<span class="dv">1981</span>), ]

<span class="co"># labels and breaks for X axis text</span>
brks &lt;- df$date[<span class="kw">seq</span>(<span class="dv">1</span>, <span class="kw">length</span>(df$date), <span class="dv">12</span>)]
lbls &lt;- lubridate::<span class="kw">year</span>(brks)

<span class="co"># plot</span>
<span class="kw">ggplot</span>(df, <span class="kw">aes</span>(<span class="dt">x=</span>date)) + 
  <span class="kw">geom_area</span>(<span class="kw">aes</span>(<span class="dt">y=</span>psavert+uempmed, <span class="dt">fill=</span><span class="st">"psavert"</span>)) + 
  <span class="kw">geom_area</span>(<span class="kw">aes</span>(<span class="dt">y=</span>uempmed, <span class="dt">fill=</span><span class="st">"uempmed"</span>)) + 
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Area Chart of Returns Percentage"</span>, 
       <span class="dt">subtitle=</span><span class="st">"From Wide Data format"</span>, 
       <span class="dt">caption=</span><span class="st">"Source: Economics"</span>, 
       <span class="dt">y=</span><span class="st">"Returns %"</span>) +  <span class="co"># title and caption</span>
  <span class="kw">scale_x_date</span>(<span class="dt">labels =</span> lbls, <span class="dt">breaks =</span> brks) +  <span class="co"># change to monthly ticks and labels</span>
  <span class="kw">scale_fill_manual</span>(<span class="dt">name=</span><span class="st">""</span>, 
                    <span class="dt">values =</span> <span class="kw">c</span>(<span class="st">"psavert"</span>=<span class="st">"#00ba38"</span>, <span class="st">"uempmed"</span>=<span class="st">"#f8766d"</span>)) +  <span class="co"># line color</span>
  <span class="kw">theme</span>(<span class="dt">panel.grid.minor =</span> <span class="kw">element_blank</span>())  <span class="co"># turn off minor grid</span></code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_41.png" alt="Stacked Area Chart in Ggplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Calendar Heatmap"></a>Calendar Heatmap</h3>
When you want to see the variation, especially the highs and lows, of a metric like stock price, on an actual calendar itself, the calendar heat map is a great tool. It emphasizes the variation visually over time rather than the actual value itself.

This can be implemented using the <code>geom_tile</code>. But getting it in the right format has more to do with the data preparation rather than the plotting itself.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># http://margintale.blogspot.in/2012/04/ggplot2-time-series-heatmaps.html</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(plyr)
<span class="kw">library</span>(scales)
<span class="kw">library</span>(zoo)

df &lt;- <span class="kw">read.csv</span>(<span class="st">"https://raw.githubusercontent.com/selva86/datasets/master/yahoo.csv"</span>)
df$date &lt;- <span class="kw">as.Date</span>(df$date)  <span class="co"># format date</span>
df &lt;- df[df$year &gt;= <span class="dv">2012</span>, ]  <span class="co"># filter reqd years</span>

<span class="co"># Create Month Week</span>
df$yearmonth &lt;- <span class="kw">as.yearmon</span>(df$date)
df$yearmonthf &lt;- <span class="kw">factor</span>(df$yearmonth)
df &lt;- <span class="kw">ddply</span>(df,.(yearmonthf), transform, <span class="dt">monthweek=</span><span class="dv">1</span>+week-<span class="kw">min</span>(week))  <span class="co"># compute week number of month</span>
df &lt;- df[, <span class="kw">c</span>(<span class="st">"year"</span>, <span class="st">"yearmonthf"</span>, <span class="st">"monthf"</span>, <span class="st">"week"</span>, <span class="st">"monthweek"</span>, <span class="st">"weekdayf"</span>, <span class="st">"VIX.Close"</span>)]
<span class="kw">head</span>(df)
<span class="co">#&gt;   year yearmonthf monthf week monthweek weekdayf VIX.Close</span>
<span class="co">#&gt; 1 2012   Jan 2012    Jan    1         1      Tue     22.97</span>
<span class="co">#&gt; 2 2012   Jan 2012    Jan    1         1      Wed     22.22</span>
<span class="co">#&gt; 3 2012   Jan 2012    Jan    1         1      Thu     21.48</span>
<span class="co">#&gt; 4 2012   Jan 2012    Jan    1         1      Fri     20.63</span>
<span class="co">#&gt; 5 2012   Jan 2012    Jan    2         2      Mon     21.07</span>
<span class="co">#&gt; 6 2012   Jan 2012    Jan    2         2      Tue     20.69</span>


<span class="co"># Plot</span>
<span class="kw">ggplot</span>(df, <span class="kw">aes</span>(monthweek, weekdayf, <span class="dt">fill =</span> VIX.Close)) + 
  <span class="kw">geom_tile</span>(<span class="dt">colour =</span> <span class="st">"white"</span>) + 
  <span class="kw">facet_grid</span>(year~monthf) + 
  <span class="kw">scale_fill_gradient</span>(<span class="dt">low=</span><span class="st">"red"</span>, <span class="dt">high=</span><span class="st">"green"</span>) +
  <span class="kw">labs</span>(<span class="dt">x=</span><span class="st">"Week of Month"</span>,
       <span class="dt">y=</span><span class="st">""</span>,
       <span class="dt">title =</span> <span class="st">"Time-Series Calendar Heatmap"</span>, 
       <span class="dt">subtitle=</span><span class="st">"Yahoo Closing Price"</span>, 
       <span class="dt">fill=</span><span class="st">"Close"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_42.png" alt="Calendar Heatmap in Ggplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Slope Chart 2"></a>Slope Chart</h3>
Slope chart is a great tool of you want to visualize change in value and ranking between categories. This is more suitable over a time series when there are very few time points.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(dplyr)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())
source_df &lt;- <span class="kw">read.csv</span>(<span class="st">"https://raw.githubusercontent.com/jkeirstead/r-slopegraph/master/cancer_survival_rates.csv"</span>)

<span class="co"># Define functions. Source: https://github.com/jkeirstead/r-slopegraph</span>
tufte_sort &lt;- function(df, <span class="dt">x=</span><span class="st">"year"</span>, <span class="dt">y=</span><span class="st">"value"</span>, <span class="dt">group=</span><span class="st">"group"</span>, <span class="dt">method=</span><span class="st">"tufte"</span>, <span class="dt">min.space=</span><span class="fl">0.05</span>) {
    ## First rename the columns for consistency
    ids &lt;- <span class="kw">match</span>(<span class="kw">c</span>(x, y, group), <span class="kw">names</span>(df))
    df &lt;- df[,ids]
    <span class="kw">names</span>(df) &lt;- <span class="kw">c</span>(<span class="st">"x"</span>, <span class="st">"y"</span>, <span class="st">"group"</span>)

    ## Expand grid to ensure every combination has a defined value
    tmp &lt;- <span class="kw">expand.grid</span>(<span class="dt">x=</span><span class="kw">unique</span>(df$x), <span class="dt">group=</span><span class="kw">unique</span>(df$group))
    tmp &lt;- <span class="kw">merge</span>(df, tmp, <span class="dt">all.y=</span><span class="ot">TRUE</span>)
    df &lt;- <span class="kw">mutate</span>(tmp, <span class="dt">y=</span><span class="kw">ifelse</span>(<span class="kw">is.na</span>(y), <span class="dv">0</span>, y))
  
    ## Cast into a matrix shape and arrange by first column
    <span class="kw">require</span>(reshape2)
    tmp &lt;- <span class="kw">dcast</span>(df, group ~ x, <span class="dt">value.var=</span><span class="st">"y"</span>)
    ord &lt;- <span class="kw">order</span>(tmp[,<span class="dv">2</span>])
    tmp &lt;- tmp[ord,]
    
    min.space &lt;- min.space*<span class="kw">diff</span>(<span class="kw">range</span>(tmp[,-<span class="dv">1</span>]))
    yshift &lt;- <span class="kw">numeric</span>(<span class="kw">nrow</span>(tmp))
    ## Start at "bottom" row
    ## Repeat for rest of the rows until you hit the top
    for (i in <span class="dv">2</span>:<span class="kw">nrow</span>(tmp)) {
        ## Shift subsequent row up by equal space so gap between
        ## two entries is &gt;= minimum
        mat &lt;- <span class="kw">as.matrix</span>(tmp[(i<span class="dv">-1</span>):i, -<span class="dv">1</span>])
        d.min &lt;- <span class="kw">min</span>(<span class="kw">diff</span>(mat))
        yshift[i] &lt;- <span class="kw">ifelse</span>(d.min &lt; min.space, min.space - d.min, <span class="dv">0</span>)
    }

    
    tmp &lt;- <span class="kw">cbind</span>(tmp, <span class="dt">yshift=</span><span class="kw">cumsum</span>(yshift))

    scale &lt;- <span class="dv">1</span>
    tmp &lt;- <span class="kw">melt</span>(tmp, <span class="dt">id=</span><span class="kw">c</span>(<span class="st">"group"</span>, <span class="st">"yshift"</span>), <span class="dt">variable.name=</span><span class="st">"x"</span>, <span class="dt">value.name=</span><span class="st">"y"</span>)
    ## Store these gaps in a separate variable so that they can be scaled ypos = a*yshift + y

    tmp &lt;- <span class="kw">transform</span>(tmp, <span class="dt">ypos=</span>y + scale*yshift)
    <span class="kw">return</span>(tmp)
   
}

plot_slopegraph &lt;- function(df) {
    ylabs &lt;- <span class="kw">subset</span>(df, x==<span class="kw">head</span>(x,<span class="dv">1</span>))$group
    yvals &lt;- <span class="kw">subset</span>(df, x==<span class="kw">head</span>(x,<span class="dv">1</span>))$ypos
    fontSize &lt;- <span class="dv">3</span>
    gg &lt;- <span class="kw">ggplot</span>(df,<span class="kw">aes</span>(<span class="dt">x=</span>x,<span class="dt">y=</span>ypos)) +
        <span class="kw">geom_line</span>(<span class="kw">aes</span>(<span class="dt">group=</span>group),<span class="dt">colour=</span><span class="st">"grey80"</span>) +
        <span class="kw">geom_point</span>(<span class="dt">colour=</span><span class="st">"white"</span>,<span class="dt">size=</span><span class="dv">8</span>) +
        <span class="kw">geom_text</span>(<span class="kw">aes</span>(<span class="dt">label=</span>y), <span class="dt">size=</span>fontSize, <span class="dt">family=</span><span class="st">"American Typewriter"</span>) +
        <span class="kw">scale_y_continuous</span>(<span class="dt">name=</span><span class="st">""</span>, <span class="dt">breaks=</span>yvals, <span class="dt">labels=</span>ylabs)
    <span class="kw">return</span>(gg)
}    

## Prepare data    
df &lt;- <span class="kw">tufte_sort</span>(source_df, 
                 <span class="dt">x=</span><span class="st">"year"</span>, 
                 <span class="dt">y=</span><span class="st">"value"</span>, 
                 <span class="dt">group=</span><span class="st">"group"</span>, 
                 <span class="dt">method=</span><span class="st">"tufte"</span>, 
                 <span class="dt">min.space=</span><span class="fl">0.05</span>)

df &lt;- <span class="kw">transform</span>(df, 
                <span class="dt">x=</span><span class="kw">factor</span>(x, <span class="dt">levels=</span><span class="kw">c</span>(<span class="dv">5</span>,<span class="dv">10</span>,<span class="dv">15</span>,<span class="dv">20</span>), 
                            <span class="dt">labels=</span><span class="kw">c</span>(<span class="st">"5 years"</span>,<span class="st">"10 years"</span>,<span class="st">"15 years"</span>,<span class="st">"20 years"</span>)), 
                <span class="dt">y=</span><span class="kw">round</span>(y))

## Plot
<span class="kw">plot_slopegraph</span>(df) + <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Estimates of % survival rates"</span>) + 
                      <span class="kw">theme</span>(<span class="dt">axis.title=</span><span class="kw">element_blank</span>(),
                            <span class="dt">axis.ticks =</span> <span class="kw">element_blank</span>(),
                            <span class="dt">plot.title =</span> <span class="kw">element_text</span>(<span class="dt">hjust=</span><span class="fl">0.5</span>,
                                                      <span class="dt">family =</span> <span class="st">"American Typewriter"</span>,
                                                      <span class="dt">face=</span><span class="st">"bold"</span>),
                            <span class="dt">axis.text =</span> <span class="kw">element_text</span>(<span class="dt">family =</span> <span class="st">"American Typewriter"</span>,
                                                     <span class="dt">face=</span><span class="st">"bold"</span>))</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_43.png" alt="Slopechart in Ggplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Seasonal Plot"></a>Seasonal Plot</h3>
If you are working with a time series object of class <code>ts</code> or <code>xts</code>, you can view the seasonal fluctuations through a seasonal plot drawn using <code>forecast::ggseasonplot</code>. Below is an example using the native <code>AirPassengers</code> and <code>nottem</code> time series.

You can see the traffic increase in air passengers over the years along with the repetitive seasonal patterns in traffic. Whereas Nottingham does not show an increase in overal temperatures over the years, but they definitely follow a seasonal pattern.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(forecast)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

<span class="co"># Subset data</span>
nottem_small &lt;- <span class="kw">window</span>(nottem, <span class="dt">start=</span><span class="kw">c</span>(<span class="dv">1920</span>, <span class="dv">1</span>), <span class="dt">end=</span><span class="kw">c</span>(<span class="dv">1925</span>, <span class="dv">12</span>))  <span class="co"># subset a smaller timewindow</span>

<span class="co"># Plot</span>
<span class="kw">ggseasonplot</span>(AirPassengers) + <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Seasonal plot: International Airline Passengers"</span>)
<span class="kw">ggseasonplot</span>(nottem_small) + <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Seasonal plot: Air temperatures at Nottingham Castle"</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_45.png" alt="Seasonal Plot in Ggplot" />
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_46.png" alt="Seasonal Plot in Ggplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h2 id="7. Groups">7. Groups</h2>
<h3><a name="Hierarchical Dendrogram"></a>Hierarchical Dendrogram</h3>
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># install.packages("ggdendro")</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(ggdendro)
<span class="kw">theme_set</span>(<span class="kw">theme_bw</span>())

hc &lt;- <span class="kw">hclust</span>(<span class="kw">dist</span>(USArrests), <span class="st">"ave"</span>)  <span class="co"># hierarchical clustering</span>

<span class="co"># plot</span>
<span class="kw">ggdendrogram</span>(hc, <span class="dt">rotate =</span> <span class="ot">TRUE</span>, <span class="dt">size =</span> <span class="dv">2</span>)</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_48.png" alt="Hierarchical Dendrogram in Ggplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3><a name="Clusters"></a>Clusters</h3>
It is possible to show the distinct clusters or groups using <code>geom_encircle()</code>. If the dataset has multiple weak features, you can compute the principal components and draw a scatterplot using PC1 and PC2 as X and Y axis.

The <code>geom_encircle()</code> can be used to encircle the desired groups. The only thing to note is the <code>data</code>argument to <code>geom_circle()</code>. You need to provide a subsetted dataframe that contains only the observations (rows) that belong to the group as the <code>data</code> argument.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># devtools::install_github("hrbrmstr/ggalt")</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(ggalt)
<span class="kw">library</span>(ggfortify)
<span class="kw">theme_set</span>(<span class="kw">theme_classic</span>())

<span class="co"># Compute data with principal components ------------------</span>
df &lt;- iris[<span class="kw">c</span>(<span class="dv">1</span>, <span class="dv">2</span>, <span class="dv">3</span>, <span class="dv">4</span>)]
pca_mod &lt;- <span class="kw">prcomp</span>(df)  <span class="co"># compute principal components</span>

<span class="co"># Data frame of principal components ----------------------</span>
df_pc &lt;- <span class="kw">data.frame</span>(pca_mod$x, <span class="dt">Species=</span>iris$Species)  <span class="co"># dataframe of principal components</span>
df_pc_vir &lt;- df_pc[df_pc$Species ==<span class="st"> "virginica"</span>, ]  <span class="co"># df for 'virginica'</span>
df_pc_set &lt;- df_pc[df_pc$Species ==<span class="st"> "setosa"</span>, ]  <span class="co"># df for 'setosa'</span>
df_pc_ver &lt;- df_pc[df_pc$Species ==<span class="st"> "versicolor"</span>, ]  <span class="co"># df for 'versicolor'</span>
 
<span class="co"># Plot ----------------------------------------------------</span>
<span class="kw">ggplot</span>(df_pc, <span class="kw">aes</span>(PC1, PC2, <span class="dt">col=</span>Species)) + 
  <span class="kw">geom_point</span>(<span class="kw">aes</span>(<span class="dt">shape=</span>Species), <span class="dt">size=</span><span class="dv">2</span>) +   <span class="co"># draw points</span>
  <span class="kw">labs</span>(<span class="dt">title=</span><span class="st">"Iris Clustering"</span>, 
       <span class="dt">subtitle=</span><span class="st">"With principal components PC1 and PC2 as X and Y axis"</span>,
       <span class="dt">caption=</span><span class="st">"Source: Iris"</span>) + 
  <span class="kw">coord_cartesian</span>(<span class="dt">xlim =</span> <span class="fl">1.2</span> * <span class="kw">c</span>(<span class="kw">min</span>(df_pc$PC1), <span class="kw">max</span>(df_pc$PC1)), 
                  <span class="dt">ylim =</span> <span class="fl">1.2</span> * <span class="kw">c</span>(<span class="kw">min</span>(df_pc$PC2), <span class="kw">max</span>(df_pc$PC2))) +   <span class="co"># change axis limits</span>
  <span class="kw">geom_encircle</span>(<span class="dt">data =</span> df_pc_vir, <span class="kw">aes</span>(<span class="dt">x=</span>PC1, <span class="dt">y=</span>PC2)) +   <span class="co"># draw circles</span>
  <span class="kw">geom_encircle</span>(<span class="dt">data =</span> df_pc_set, <span class="kw">aes</span>(<span class="dt">x=</span>PC1, <span class="dt">y=</span>PC2)) + 
  <span class="kw">geom_encircle</span>(<span class="dt">data =</span> df_pc_ver, <span class="kw">aes</span>(<span class="dt">x=</span>PC1, <span class="dt">y=</span>PC2))</code></pre>
</div>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_49.png" alt="Clustering in Ggplot" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h2 id="8. Spatial">8. Spatial</h2>
The <code>ggmap</code> package provides facilities to interact with the google maps api and get the coordinates (latitude and longitude) of places you want to plot. The below example shows satellite, road and hybrid maps of the city of Chennai, encircling some of the places. I used the <code>geocode()</code> function to get the coordinates of these places and <code>qmap()</code> to get the maps. The type of map to fetch is determined by the value you set to the <code>maptype</code>.

You can also zoom into the map by setting the <code>zoom</code> argument. The default is 10 (suitable for large cities). Reduce this number (up to 3) if you want to zoom out. It can be zoomed in till 21, suitable for buildings.
<div class="sourceCode">
<pre class="sourceCode r"><code class="sourceCode r"><span class="co"># Better install the dev versions ----------</span>
<span class="co"># devtools::install_github("dkahle/ggmap")</span>
<span class="co"># devtools::install_github("hrbrmstr/ggalt")</span>

<span class="co"># load packages</span>
<span class="kw">library</span>(ggplot2)
<span class="kw">library</span>(ggmap)
<span class="kw">library</span>(ggalt)

<span class="co"># Get Chennai's Coordinates --------------------------------</span>
chennai &lt;-  <span class="kw">geocode</span>(<span class="st">"Chennai"</span>)  <span class="co"># get longitude and latitude</span>

<span class="co"># Get the Map ----------------------------------------------</span>
<span class="co"># Google Satellite Map</span>
chennai_ggl_sat_map &lt;- <span class="kw">qmap</span>(<span class="st">"chennai"</span>, <span class="dt">zoom=</span><span class="dv">12</span>, <span class="dt">source =</span> <span class="st">"google"</span>, <span class="dt">maptype=</span><span class="st">"satellite"</span>)  

<span class="co"># Google Road Map</span>
chennai_ggl_road_map &lt;- <span class="kw">qmap</span>(<span class="st">"chennai"</span>, <span class="dt">zoom=</span><span class="dv">12</span>, <span class="dt">source =</span> <span class="st">"google"</span>, <span class="dt">maptype=</span><span class="st">"roadmap"</span>)  

<span class="co"># Google Hybrid Map</span>
chennai_ggl_hybrid_map &lt;- <span class="kw">qmap</span>(<span class="st">"chennai"</span>, <span class="dt">zoom=</span><span class="dv">12</span>, <span class="dt">source =</span> <span class="st">"google"</span>, <span class="dt">maptype=</span><span class="st">"hybrid"</span>)  

<span class="co"># Open Street Map</span>
chennai_osm_map &lt;- <span class="kw">qmap</span>(<span class="st">"chennai"</span>, <span class="dt">zoom=</span><span class="dv">12</span>, <span class="dt">source =</span> <span class="st">"osm"</span>)   

<span class="co"># Get Coordinates for Chennai's Places ---------------------</span>
chennai_places &lt;- <span class="kw">c</span>(<span class="st">"Kolathur"</span>,
                    <span class="st">"Washermanpet"</span>,
                    <span class="st">"Royapettah"</span>,
                    <span class="st">"Adyar"</span>,
                    <span class="st">"Guindy"</span>)

places_loc &lt;- <span class="kw">geocode</span>(chennai_places)  <span class="co"># get longitudes and latitudes</span>


<span class="co"># Plot Open Street Map -------------------------------------</span>
chennai_osm_map + <span class="kw">geom_point</span>(<span class="kw">aes</span>(<span class="dt">x=</span>lon, <span class="dt">y=</span>lat),
                             <span class="dt">data =</span> places_loc, 
                             <span class="dt">alpha =</span> <span class="fl">0.7</span>, 
                             <span class="dt">size =</span> <span class="dv">7</span>, 
                             <span class="dt">color =</span> <span class="st">"tomato"</span>) + 
                  <span class="kw">geom_encircle</span>(<span class="kw">aes</span>(<span class="dt">x=</span>lon, <span class="dt">y=</span>lat),
                                <span class="dt">data =</span> places_loc, <span class="dt">size =</span> <span class="dv">2</span>, <span class="dt">color =</span> <span class="st">"blue"</span>)

<span class="co"># Plot Google Road Map -------------------------------------</span>
chennai_ggl_road_map + <span class="kw">geom_point</span>(<span class="kw">aes</span>(<span class="dt">x=</span>lon, <span class="dt">y=</span>lat),
                                  <span class="dt">data =</span> places_loc, 
                                  <span class="dt">alpha =</span> <span class="fl">0.7</span>, 
                                  <span class="dt">size =</span> <span class="dv">7</span>, 
                                  <span class="dt">color =</span> <span class="st">"tomato"</span>) + 
                       <span class="kw">geom_encircle</span>(<span class="kw">aes</span>(<span class="dt">x=</span>lon, <span class="dt">y=</span>lat),
                                     <span class="dt">data =</span> places_loc, <span class="dt">size =</span> <span class="dv">2</span>, <span class="dt">color =</span> <span class="st">"blue"</span>)

<span class="co"># Google Hybrid Map ----------------------------------------</span>
chennai_ggl_hybrid_map + <span class="kw">geom_point</span>(<span class="kw">aes</span>(<span class="dt">x=</span>lon, <span class="dt">y=</span>lat),
                                     <span class="dt">data =</span> places_loc, 
                                     <span class="dt">alpha =</span> <span class="fl">0.7</span>, 
                                     <span class="dt">size =</span> <span class="dv">7</span>, 
                                     <span class="dt">color =</span> <span class="st">"tomato"</span>) + 
                          <span class="kw">geom_encircle</span>(<span class="kw">aes</span>(<span class="dt">x=</span>lon, <span class="dt">y=</span>lat),
                                        <span class="dt">data =</span> places_loc, <span class="dt">size =</span> <span class="dv">2</span>, <span class="dt">color =</span> <span class="st">"blue"</span>)</code></pre>
</div>
<h3>Open Street Map<a name="Open Street Map"></a></h3>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_50.png" alt="Spatial Map in Ggplot2 Ggmap" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3>Google Road Map<a name="Google Road Map"></a></h3>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_51.png" alt="Google Road Map in Ggplot2 Ggmap" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>
<h3>Google Hybrid Map<a name="Google Hybrid Map"></a></h3>
<img src="http://the-r.kr/wp-content/uploads/2017/03/ggplot_masterlist_52.png" alt="Google Hybrid Map in Ggplot2 Ggmap" />

<a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html#top">[Back to Top]</a>

소스: <em><a href="http://r-statistics.co/Top50-Ggplot2-Visualizations-MasterList-R-Code.html">Top 50 ggplot2 Visualizations - The Master List (With Full R Code)</a></em>