---
ID: 1456
post_title: 'Scatterplot3d : 3D 그래픽 &#8211; R 소프트웨어 및 데이터 시각화 &#8211; 쉬운 안내서'
author: The-R
post_date: 2017-02-25 13:00:52
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/02/25/scatterplot3d-3d-%ea%b7%b8%eb%9e%98%ed%94%bd-r-%ec%86%8c%ed%94%84%ed%8a%b8%ec%9b%a8%ec%96%b4-%eb%b0%8f-%eb%8d%b0%ec%9d%b4%ed%84%b0-%ec%8b%9c%ea%b0%81%ed%99%94-%ec%89%ac%ec%9a%b4-%ec%95%88/'
published: true
inline_featured_image:
  - "0"
---
There are many packages in R (<em>RGL</em>, <em>car</em>, <em>lattice</em>, <em>scatterplot3d</em>, …) for creating <strong>3D graphics</strong>.

This <strong>tutorial</strong> describes how to generate a scatter pot in the <strong>3D space</strong> using <strong>R software</strong> and the package <strong>scatterplot3d</strong>.

<strong>scaterplot3d</strong> is very simple to use and it can be easily extended by adding supplementary points or regression planes into an already generated graphic.

It can be easily installed, as it requires only an installed version of R.

<img src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d.gif" alt="3d scatter plot" />
<div id="install-and-load-scaterplot3d" class="section level1">
<h1 class="wiki_paragraph1">Install and load scaterplot3d</h1>
<pre class="r"><code class="r"><span class="identifier">install.packages</span><span class="paren">(</span><span class="string">"scatterplot3d"</span><span class="paren">)</span> <span class="comment"># Install</span>
<span class="keyword">library</span><span class="paren">(</span><span class="string">"scatterplot3d"</span><span class="paren">)</span> <span class="comment"># load</span></code></pre>
</div>
<div id="prepare-the-data" class="section level1">
<h1 class="wiki_paragraph1">Prepare the data</h1>
The <em>iris</em> data set will be used:
<pre class="r"><code class="r"><span class="identifier">data</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">)</span>
<span class="keyword">head</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">)</span></code></pre>
<pre><code>  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa</code></pre>
<span class="notice"><em>iris</em> data set gives the measurements of the variables sepal length and width, petal length and width, respectively, for 50 flowers from each of 3 species of iris. The species are Iris setosa, versicolor, and virginica.</span>

</div>
<div id="the-function-scatterplot3d" class="section level1">
<h1 class="wiki_paragraph1">The function scatterplot3d()</h1>
A simplified format is:
<pre class="r"><code class="r"><span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">x</span>, <span class="identifier">y</span><span class="operator">=</span><span class="literal">NULL</span>, <span class="identifier">z</span><span class="operator">=</span><span class="literal">NULL</span><span class="paren">)</span></code></pre>
<span class="success">x, y, z are the coordinates of points to be plotted. The arguments <em>y</em> and <em>z</em> can be optional depending on the structure of <em>x</em>.</span>

<span class="question">In what cases, <em>y</em> and <em>z</em> are optional variables?</span>
<ul>
 	<li><strong>Case 1 : x is a formula</strong> of type <em>zvar ~ xvar + yvar</em>. xvar, yvar and zvar are used as x, y and z variables</li>
 	<li><strong>Case 2 : x is a matrix</strong> containing at least 3 columns corresponding to x, y and z variables, respectively</li>
</ul>
</div>
<div id="basic-3d-scatter-plots" class="section level1">
<h1 class="wiki_paragraph1">Basic 3D scatter plots</h1>
<pre class="r"><code class="r"><span class="comment"># Basic 3d graphics</span>
<span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-scatter-plot-3d-r-data-visualization-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />
<pre class="r"><code class="r"><span class="comment"># Change the angle of point view</span>
<span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">angle</span> <span class="operator">=</span> <span class="number">55</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-scatter-plot-3d-r-data-visualization-2.png" alt="Scatterplot3d - R software and data visualization" width="432" />

</div>
<div id="change-the-main-title-and-axis-labels" class="section level1">
<h1 class="wiki_paragraph1">Change the main title and axis labels</h1>
<pre class="r"><code class="r"><span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>,
              <span class="identifier">main</span><span class="operator">=</span><span class="string">"3D Scatter Plot"</span>,
              <span class="identifier">xlab</span> <span class="operator">=</span> <span class="string">"Sepal Length (cm)"</span>,
              <span class="identifier">ylab</span> <span class="operator">=</span> <span class="string">"Sepal Width (cm)"</span>,
              <span class="identifier">zlab</span> <span class="operator">=</span> <span class="string">"Petal Length (cm)"</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-title-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />

</div>
<div id="change-the-shape-and-the-color-of-points" class="section level1">
<h1 class="wiki_paragraph1">Change the shape and the color of points</h1>
The argument <em>pch</em> and <em>color</em> can be used:
<pre class="r"><code class="r"><span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, <span class="identifier">color</span><span class="operator">=</span><span class="string">"steelblue"</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-scatter-plot-3d-shape-r-data-visualization-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />

Read more on the different point shapes available in R : <a href="http://www.sthda.com/english/wiki/r-plot-pch-symbols-the-different-point-shapes-available-in-r">Point shapes in R</a>

</div>
<div id="change-point-shapes-by-groups" class="section level1">
<h1 class="wiki_paragraph1">Change point shapes by groups</h1>
<pre class="r"><code class="r"><span class="identifier">shapes</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="number">16</span>, <span class="number">17</span>, <span class="number">18</span><span class="paren">)</span> 
<span class="identifier">shapes</span> <span class="operator">&lt;-</span> <span class="identifier">shapes</span><span class="paren">[</span><span class="identifier">as.numeric</span><span class="paren">(</span><span class="identifier">iris</span><span class="operator">$</span><span class="identifier">Species</span><span class="paren">)</span><span class="paren">]</span>
<span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="identifier">shapes</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-scatter-plot-3d-shape-by-groups-r-data-visualization-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />

Read more on the different point shapes available in R : <a href="http://www.sthda.com/english/wiki/r-plot-pch-symbols-the-different-point-shapes-available-in-r">Point shapes in R</a>

</div>
<div id="change-point-colors-by-groups" class="section level1">
<h1 class="wiki_paragraph1">Change point colors by groups</h1>
<pre class="r"><code class="r"><span class="identifier">colors</span> <span class="operator">&lt;-</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"#999999"</span>, <span class="string">"#E69F00"</span>, <span class="string">"#56B4E9"</span><span class="paren">)</span>
<span class="identifier">colors</span> <span class="operator">&lt;-</span> <span class="identifier">colors</span><span class="paren">[</span><span class="identifier">as.numeric</span><span class="paren">(</span><span class="identifier">iris</span><span class="operator">$</span><span class="identifier">Species</span><span class="paren">)</span><span class="paren">]</span>
<span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, <span class="identifier">color</span><span class="operator">=</span><span class="identifier">colors</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-scatter-plot-3d-color-by-groups-r-data-visualization-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />

Read more about colors in R: <a href="http://www.sthda.com/english/wiki/colors-in-r">colors in R</a>

</div>
<div id="change-the-global-appearance-of-the-graph" class="section level1">
<h1 class="wiki_paragraph1">Change the global appearance of the graph</h1>
The arguments below can be used:
<ul>
 	<li><strong>grid</strong>: a logical value. If TRUE, a grid is drawn on the plot.</li>
 	<li><strong>box</strong>: a logical value. If TRUE, a box is drawn around the plot</li>
</ul>
<div id="remove-the-box-around-the-plot" class="section level2">
<h2 class="wiki_paragraph2">Remove the box around the plot</h2>
<pre class="r"><code class="r"><span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, <span class="identifier">color</span> <span class="operator">=</span> <span class="identifier">colors</span>,
              <span class="identifier">grid</span><span class="operator">=</span><span class="literal">TRUE</span>, <span class="identifier">box</span><span class="operator">=</span><span class="literal">FALSE</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-remove-box-grid-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />

<span class="warning">Note that, the argument <strong>grid = TRUE</strong> plots only the grid on the xy plane. In the next section, we’ll see how to add grids on the other facets of the 3D scatter plot.</span>

</div>
<div id="add-grids-on-scatterplot3d" class="section level2">
<h2 class="wiki_paragraph2">Add grids on scatterplot3d</h2>
This section describes how to add <em>xy-</em>, <em>xz-</em> and <em>yz-</em> to <strong>scatterplot3d</strong> graphics.

We’ll use a custom function named <strong>addgrids3d()</strong>. The source code is available here : <a href="http://www.sthda.com/sthda/RDoc/functions/addgrids3d.r">addgrids3d.r</a>. The function is inspired from the discussion on this <a href="http://stackoverflow.com/questions/20448539/add-yz-and-xz-grid-to-scatterplot3d">forum</a>.

A simplified format of the function is:
<pre class="r"><code class="r"><span class="identifier">addgrids3d</span><span class="paren">(</span><span class="identifier">x</span>, <span class="identifier">y</span><span class="operator">=</span><span class="literal">NULL</span>, <span class="identifier">z</span><span class="operator">=</span><span class="literal">NULL</span>, <span class="identifier">grid</span> <span class="operator">=</span> <span class="literal">TRUE</span>,
           <span class="identifier">col.grid</span> <span class="operator">=</span> <span class="string">"grey"</span>, <span class="identifier">lty.grid</span><span class="operator">=</span><span class="identifier">par</span><span class="paren">(</span><span class="string">"lty"</span><span class="paren">)</span><span class="paren">)</span></code></pre>
<div class="block">
<ul>
 	<li><strong>x, y, and z</strong> are numeric vectors specifying the x, y, z coordinates of points. x can be a matrix or a data frame containing 3 columns corresponding to the x, y and z coordinates. In this case the arguments y and z are optional</li>
 	<li><strong>grid</strong> specifies the facet(s) of the plot on which grids should be drawn. Possible values are the combination of “xy”, “xz” or “yz”. Example: grid = c(“xy”, “yz”). The default value is TRUE to add grids only on xy facet.</li>
 	<li><strong>col.grid, lty.grid</strong>: the color and the line type to be used for grids</li>
</ul>
</div>
<strong>Add grids on the different factes of scatterplot3d graphics</strong>:
<pre class="r"><code class="r"><span class="comment"># 1. Source the function</span>
<span class="keyword">source</span><span class="paren">(</span><span class="string">'http://www.sthda.com/sthda/RDoc/functions/addgrids3d.r'</span><span class="paren">)</span>
<span class="comment"># 2. 3D scatter plot</span>
<span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>, <span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, <span class="identifier">grid</span><span class="operator">=</span><span class="literal">FALSE</span>, <span class="identifier">box</span><span class="operator">=</span><span class="literal">FALSE</span><span class="paren">)</span>
<span class="comment"># 3. Add grids</span>
<span class="identifier">addgrids3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>, <span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">grid</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"xy"</span>, <span class="string">"xz"</span>, <span class="string">"yz"</span><span class="paren">)</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-add-grids-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />

<span class="warning">The problem on the above plot is that the grids are drawn over the points.</span>

The <strong>R code</strong> below, we’ll put the points in the foreground using the following steps:
<ol>
 	<li>An empty scatterplot3 graphic is created and the result of <strong>scatterplot3d()</strong> is assigned to <em>s3d</em></li>
 	<li>The function <strong>addgrids3d()</strong> is used to add grids</li>
 	<li>Finally, the function <strong>s3d$points3d</strong> is used to add points on the 3D scatter plot</li>
</ol>
<pre class="r"><code class="r"><span class="comment"># 1. Source the function</span>
<span class="keyword">source</span><span class="paren">(</span><span class="string">'~/hubiC/Documents/R/function/addgrids3d.r'</span><span class="paren">)</span>
<span class="comment"># 2. Empty 3D scatter plot using pch=""</span>
<span class="identifier">s3d</span> <span class="operator">&lt;-</span> <span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>, <span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="string">""</span>, <span class="identifier">grid</span><span class="operator">=</span><span class="literal">FALSE</span>, <span class="identifier">box</span><span class="operator">=</span><span class="literal">FALSE</span><span class="paren">)</span>
<span class="comment"># 3. Add grids</span>
<span class="identifier">addgrids3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>, <span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">grid</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"xy"</span>, <span class="string">"xz"</span>, <span class="string">"yz"</span><span class="paren">)</span><span class="paren">)</span>
<span class="comment"># 4. Add points</span>
<span class="identifier">s3d</span><span class="operator">$</span><span class="identifier">points3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>, <span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-add-grids2-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />

<span class="notice">The function <strong>points3d()</strong> is described in the next sections.</span>

</div>
</div>
<div id="add-bars" class="section level1">
<h1 class="wiki_paragraph1">Add bars</h1>
The argument <strong>type = “h”</strong> is used. This is useful to see very clearly the x-y location of points.
<pre class="r"><code class="r"><span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, <span class="identifier">type</span><span class="operator">=</span><span class="string">"h"</span>, 
              <span class="identifier">color</span><span class="operator">=</span><span class="identifier">colors</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-add-bars-r-data-visualization-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />

</div>
<div id="modification-of-scatterplot3d-output" class="section level1">
<h1 class="wiki_paragraph1">Modification of scatterplot3d output</h1>
<strong>scatterplot3d</strong> returns a list of function closures which can be used to add elements on a existing plot.

The returned functions are :
<ul>
 	<li><strong>xyz.convert()</strong>: to convert 3D coordinates to the 2D parallel projection of the existing scatterplot3d. It can be used to add arbitrary elements, such as legend, into the plot.</li>
 	<li><strong>points3d()</strong>: to add <em>points</em> or <em>lines</em> into the existing plot</li>
 	<li><strong>plane3d()</strong>: to add a <em>plane</em> into the existing plot</li>
 	<li><strong>box3d()</strong>: to add or refresh a <em>box</em> around the plot</li>
</ul>
<div id="add-legends" class="section level2">
<h2 class="wiki_paragraph2">Add legends</h2>
<div id="specify-the-legend-position-using-xyz.convert" class="section level3">
<h3 class="wiki_paragraph3">Specify the legend position using xyz.convert()</h3>
<ol>
 	<li>The result of <strong>scatterplot3d()</strong> is assigned to <em>s3d</em></li>
 	<li>The function <strong>s3d$xyz.convert()</strong> is used to specify the coordinates for legends</li>
 	<li>the function <strong>legend()</strong> is used to add legends to plots</li>
</ol>
<pre class="r"><code class="r"><span class="identifier">s3d</span> <span class="operator">&lt;-</span> <span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, <span class="identifier">color</span><span class="operator">=</span><span class="identifier">colors</span><span class="paren">)</span>
<span class="identifier">legend</span><span class="paren">(</span><span class="identifier">s3d</span><span class="operator">$</span><span class="identifier">xyz.convert</span><span class="paren">(</span><span class="number">7.5</span>, <span class="number">3</span>, <span class="number">4.5</span><span class="paren">)</span>, <span class="identifier">legend</span> <span class="operator">=</span> <span class="identifier">levels</span><span class="paren">(</span><span class="identifier">iris</span><span class="operator">$</span><span class="identifier">Species</span><span class="paren">)</span>,
      <span class="identifier">col</span> <span class="operator">=</span>  <span class="identifier">c</span><span class="paren">(</span><span class="string">"#999999"</span>, <span class="string">"#E69F00"</span>, <span class="string">"#56B4E9"</span><span class="paren">)</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-add-legend-r-data-visualization-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />
<div class="block">

It’s also possible to specify the <strong>position of legends</strong> using the following keywords: “bottomright”, “bottom”, “bottomleft”, “left”, “topleft”, “top”, “topright”, “right” and “center”.

Read more about <strong>legend</strong> in R: <a href="http://www.sthda.com/english/wiki/add-legends-to-plots-in-r-software-the-easiest-way">legend in R</a>.</div>
</div>
<div id="specify-the-legend-position-using-keywords" class="section level3">
<h3 class="wiki_paragraph3">Specify the legend position using keywords</h3>
<pre class="r"><code class="r"><span class="comment"># "right" position</span>
<span class="identifier">s3d</span> <span class="operator">&lt;-</span> <span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, <span class="identifier">color</span><span class="operator">=</span><span class="identifier">colors</span><span class="paren">)</span>
<span class="identifier">legend</span><span class="paren">(</span><span class="string">"right"</span>, <span class="identifier">legend</span> <span class="operator">=</span> <span class="identifier">levels</span><span class="paren">(</span><span class="identifier">iris</span><span class="operator">$</span><span class="identifier">Species</span><span class="paren">)</span>,
      <span class="identifier">col</span> <span class="operator">=</span>  <span class="identifier">c</span><span class="paren">(</span><span class="string">"#999999"</span>, <span class="string">"#E69F00"</span>, <span class="string">"#56B4E9"</span><span class="paren">)</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-change-legend-position-right-r-data-visualization-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />
<pre class="r"><code class="r"><span class="comment"># Use the argument inset</span>
<span class="identifier">s3d</span> <span class="operator">&lt;-</span> <span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, <span class="identifier">color</span><span class="operator">=</span><span class="identifier">colors</span><span class="paren">)</span>
<span class="identifier">legend</span><span class="paren">(</span><span class="string">"right"</span>, <span class="identifier">legend</span> <span class="operator">=</span> <span class="identifier">levels</span><span class="paren">(</span><span class="identifier">iris</span><span class="operator">$</span><span class="identifier">Species</span><span class="paren">)</span>,
  <span class="identifier">col</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"#999999"</span>, <span class="string">"#E69F00"</span>, <span class="string">"#56B4E9"</span><span class="paren">)</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, <span class="identifier">inset</span> <span class="operator">=</span> <span class="number">0.1</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-change-legend-position-right-r-data-visualization-2.png" alt="Scatterplot3d - R software and data visualization" width="432" />

<span class="question">What means the argument <strong>inset</strong> in the R code above?</span>

The argument <strong>inset</strong> is used to inset distance(s) from the margins as a fraction of the plot region when legend is positioned by keyword. ( see ?legend from R). You can play with <em>inset</em> argument using negative or positive values.
<pre class="r"><code class="r"><span class="comment"># "bottom" position</span>
<span class="identifier">s3d</span> <span class="operator">&lt;-</span> <span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, <span class="identifier">color</span><span class="operator">=</span><span class="identifier">colors</span><span class="paren">)</span>
<span class="identifier">legend</span><span class="paren">(</span><span class="string">"bottom"</span>, <span class="identifier">legend</span> <span class="operator">=</span> <span class="identifier">levels</span><span class="paren">(</span><span class="identifier">iris</span><span class="operator">$</span><span class="identifier">Species</span><span class="paren">)</span>,
      <span class="identifier">col</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"#999999"</span>, <span class="string">"#E69F00"</span>, <span class="string">"#56B4E9"</span><span class="paren">)</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-change-legend-position-r-data-visualization-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />

Using <em>keywords</em> to specify the <em>legend position</em> is very simple. However, sometimes, there is an overlap between some points and the legend box or between the axis and legend box.

<span class="question">Is there any solution to avoid this overlap?</span>

Yes, there are several solutions using the combination of the following arguments for the function <strong>legend()</strong>:
<ul>
 	<li><strong>bty = “n”</strong> : to <strong>remove the box around the legend</strong>. In this case the background color of the legend becomes transparent and the overlapping points become visible.</li>
 	<li><strong>bg = “transparent”</strong>: to change the background color of the legend box to <em>transparent</em> color (this is only possible when bty != “n”).</li>
 	<li><strong>inset</strong>: to modify the distance(s) between plot margins and the legend box.</li>
 	<li><strong>horiz</strong>: a logical value; if TRUE, set the legend horizontally rather than vertically</li>
 	<li><strong>xpd</strong>: a logical value; if TRUE, it enables the legend items to be drawn outside the plot.</li>
</ul>
</div>
<div id="customize-the-legend-position" class="section level3">
<h3 class="wiki_paragraph3">Customize the legend position</h3>
<pre class="r"><code class="r"><span class="comment"># Custom point shapes</span>
<span class="identifier">s3d</span> <span class="operator">&lt;-</span> <span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="identifier">shapes</span><span class="paren">)</span>
<span class="identifier">legend</span><span class="paren">(</span><span class="string">"bottom"</span>, <span class="identifier">legend</span> <span class="operator">=</span> <span class="identifier">levels</span><span class="paren">(</span><span class="identifier">iris</span><span class="operator">$</span><span class="identifier">Species</span><span class="paren">)</span>,
       <span class="identifier">pch</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="number">16</span>, <span class="number">17</span>, <span class="number">18</span><span class="paren">)</span>, 
      <span class="identifier">inset</span> <span class="operator">=</span> <span class="operator">-</span><span class="number">0.25</span>, <span class="identifier">xpd</span> <span class="operator">=</span> <span class="literal">TRUE</span>, <span class="identifier">horiz</span> <span class="operator">=</span> <span class="literal">TRUE</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-custom-legend-position-r-data-visualization-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />
<pre class="r"><code class="r"><span class="comment"># Custom colors</span>
<span class="identifier">s3d</span> <span class="operator">&lt;-</span> <span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, <span class="identifier">color</span><span class="operator">=</span><span class="identifier">colors</span><span class="paren">)</span>
<span class="identifier">legend</span><span class="paren">(</span><span class="string">"bottom"</span>, <span class="identifier">legend</span> <span class="operator">=</span> <span class="identifier">levels</span><span class="paren">(</span><span class="identifier">iris</span><span class="operator">$</span><span class="identifier">Species</span><span class="paren">)</span>,
      <span class="identifier">col</span> <span class="operator">=</span>  <span class="identifier">c</span><span class="paren">(</span><span class="string">"#999999"</span>, <span class="string">"#E69F00"</span>, <span class="string">"#56B4E9"</span><span class="paren">)</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, 
      <span class="identifier">inset</span> <span class="operator">=</span> <span class="operator">-</span><span class="number">0.25</span>, <span class="identifier">xpd</span> <span class="operator">=</span> <span class="literal">TRUE</span>, <span class="identifier">horiz</span> <span class="operator">=</span> <span class="literal">TRUE</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-custom-legend-position-r-data-visualization-2.png" alt="Scatterplot3d - R software and data visualization" width="432" />
<pre class="r"><code class="r"><span class="comment"># Custom shapes/colors</span>
<span class="identifier">s3d</span> <span class="operator">&lt;-</span> <span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="identifier">shapes</span>, <span class="identifier">color</span><span class="operator">=</span><span class="identifier">colors</span><span class="paren">)</span>
<span class="identifier">legend</span><span class="paren">(</span><span class="string">"bottom"</span>, <span class="identifier">legend</span> <span class="operator">=</span> <span class="identifier">levels</span><span class="paren">(</span><span class="identifier">iris</span><span class="operator">$</span><span class="identifier">Species</span><span class="paren">)</span>,
      <span class="identifier">col</span> <span class="operator">=</span>  <span class="identifier">c</span><span class="paren">(</span><span class="string">"#999999"</span>, <span class="string">"#E69F00"</span>, <span class="string">"#56B4E9"</span><span class="paren">)</span>, 
      <span class="identifier">pch</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="number">16</span>, <span class="number">17</span>, <span class="number">18</span><span class="paren">)</span>, 
      <span class="identifier">inset</span> <span class="operator">=</span> <span class="operator">-</span><span class="number">0.25</span>, <span class="identifier">xpd</span> <span class="operator">=</span> <span class="literal">TRUE</span>, <span class="identifier">horiz</span> <span class="operator">=</span> <span class="literal">TRUE</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-custom-legend-position-r-data-visualization-3.png" alt="Scatterplot3d - R software and data visualization" width="432" />

<span class="notice">In the R code above, you can play with the arguments <em>inset</em>, <em>xpd</em> and <em>horiz</em> to see the effects on the appearance of the legend box.</span>

</div>
</div>
<div id="add-point-labels" class="section level2">
<h2 class="wiki_paragraph2">Add point labels</h2>
The function <strong>text()</strong> is used as follow:
<pre class="r"><code class="r"><span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>,<span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span>, <span class="identifier">color</span><span class="operator">=</span><span class="identifier">colors</span><span class="paren">)</span>
<span class="identifier">text</span><span class="paren">(</span><span class="identifier">s3d</span><span class="operator">$</span><span class="identifier">xyz.convert</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">[</span>, <span class="number">1</span><span class="operator">:</span><span class="number">3</span><span class="paren">]</span><span class="paren">)</span>, <span class="identifier">labels</span> <span class="operator">=</span> <span class="identifier">rownames</span><span class="paren">(</span><span class="identifier">iris</span><span class="paren">)</span>,
     <span class="identifier">cex</span><span class="operator">=</span> <span class="number">0.7</span>, <span class="identifier">col</span> <span class="operator">=</span> <span class="string">"steelblue"</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-text-r-data-visualization-1.png" alt="Scatterplot3d - R software and data visualization" width="432" />

</div>
<div id="add-regression-plane-and-supplementary-points" class="section level2">
<h2 class="wiki_paragraph2">Add regression plane and supplementary points</h2>
<ol>
 	<li>The result of <strong>scatterplot3d()</strong> is assigned to <em>s3d</em></li>
 	<li>A linear model is calculated as follow : lm(zvar ~ xvar + yvar). Assumption : zvar depends on xvar and yvar</li>
 	<li>The function <strong>s3d$plane3d()</strong> is used to add the regression plane</li>
 	<li>Supplementary points are added using the function <strong>s3d$points3d()</strong></li>
</ol>
The data sets <em>trees</em> will be used:
<pre class="r"><code class="r"><span class="identifier">data</span><span class="paren">(</span><span class="identifier">trees</span><span class="paren">)</span>
<span class="keyword">head</span><span class="paren">(</span><span class="identifier">trees</span><span class="paren">)</span></code></pre>
<pre><code>  Girth Height Volume
1   8.3     70   10.3
2   8.6     65   10.3
3   8.8     63   10.2
4  10.5     72   16.4
5  10.7     81   18.8
6  10.8     83   19.7</code></pre>
<span class="notice">This data set provides measurements of the girth, height and volume for black cherry trees.</span>

<strong>3D scatter plot with the regression plane</strong>:
<pre class="r"><code class="r"><span class="comment"># 3D scatter plot</span>
<span class="identifier">s3d</span> <span class="operator">&lt;-</span> <span class="identifier">scatterplot3d</span><span class="paren">(</span><span class="identifier">trees</span>, <span class="identifier">type</span> <span class="operator">=</span> <span class="string">"h"</span>, <span class="identifier">color</span> <span class="operator">=</span> <span class="string">"blue"</span>,
    <span class="identifier">angle</span><span class="operator">=</span><span class="number">55</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">16</span><span class="paren">)</span>
<span class="comment"># Add regression plane</span>
<span class="identifier">my.lm</span> <span class="operator">&lt;-</span> <span class="identifier">lm</span><span class="paren">(</span><span class="identifier">trees</span><span class="operator">$</span><span class="identifier">Volume</span> <span class="operator">~</span> <span class="identifier">trees</span><span class="operator">$</span><span class="identifier">Girth</span> <span class="operator">+</span> <span class="identifier">trees</span><span class="operator">$</span><span class="identifier">Height</span><span class="paren">)</span>
<span class="identifier">s3d</span><span class="operator">$</span><span class="identifier">plane3d</span><span class="paren">(</span><span class="identifier">my.lm</span><span class="paren">)</span>
<span class="comment"># Add supplementary points</span>
<span class="identifier">s3d</span><span class="operator">$</span><span class="identifier">points3d</span><span class="paren">(</span><span class="identifier">seq</span><span class="paren">(</span><span class="number">10</span>, <span class="number">20</span>, <span class="number">2</span><span class="paren">)</span>, <span class="identifier">seq</span><span class="paren">(</span><span class="number">85</span>, <span class="number">60</span>, <span class="operator">-</span><span class="number">5</span><span class="paren">)</span>, <span class="identifier">seq</span><span class="paren">(</span><span class="number">60</span>, <span class="number">10</span>, <span class="operator">-</span><span class="number">10</span><span class="paren">)</span>,
    <span class="identifier">col</span> <span class="operator">=</span> <span class="string">"red"</span>, <span class="identifier">type</span> <span class="operator">=</span> <span class="string">"h"</span>, <span class="identifier">pch</span> <span class="operator">=</span> <span class="number">8</span><span class="paren">)</span></code></pre>
<img title="Scatterplot3d - R software and data visualization" src="http://the-r.kr/wp-content/uploads/2017/02/scatterplot3d-regression-plane-1.png" alt="Scatterplot3d - R software and data visualization" width="480" />

</div>
</div>
소스: <em><a href="http://www.sthda.com/english/wiki/scatterplot3d-3d-graphics-r-software-and-data-visualization">Scatterplot3d: 3D graphics - R software and data visualization - Easy Guides - Wiki - STHDA</a></em>