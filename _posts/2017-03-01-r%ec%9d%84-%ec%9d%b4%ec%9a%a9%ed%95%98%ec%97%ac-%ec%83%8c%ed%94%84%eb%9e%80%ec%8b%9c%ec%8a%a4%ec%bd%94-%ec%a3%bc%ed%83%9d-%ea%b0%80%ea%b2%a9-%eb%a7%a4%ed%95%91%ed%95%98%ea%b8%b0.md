---
ID: 1528
post_title: >
  R을 이용하여 샌프란시스코
  주택 가격 매핑하기
author: The-R
post_date: 2017-03-01 20:45:28
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/03/01/r%ec%9d%84-%ec%9d%b4%ec%9a%a9%ed%95%98%ec%97%ac-%ec%83%8c%ed%94%84%eb%9e%80%ec%8b%9c%ec%8a%a4%ec%bd%94-%ec%a3%bc%ed%83%9d-%ea%b0%80%ea%b2%a9-%eb%a7%a4%ed%95%91%ed%95%98%ea%b8%b0/'
published: true
inline_featured_image:
  - "0"
---
<blockquote>At the intersection of data science &amp; public policy</blockquote>
<strong>Authors: Ken Steif &amp; Simon Kassel</strong>

I constantly preach to my students that no matter how policy relevant your work is, if it cannot be conveyed to a non-technical decision maker, it isn’t useful. This underlies why data visualization is such an important tool for data scientists.

Because so much public policy has spatial implications, much of the data visualization we produce at Urban Spatial is geographic in nature.

My colleague Simon and I recently worked together on a <a href="http://urbanspatialanalysis.com/portfolio/predicting-gentrification-using-longitudinal-census-data/">machine learning model of gentrification</a> using Census data throughout the U.S. In that piece we discuss the importance of parcel level data.

We thought we’d revisit the subject here using higher resolution data and report on our findings by way of data visualization.

Given our mutual interest in making maps in R, in this piece, <a href="https://github.com/simonkassel/Visualizing_SF_home_prices_R/blob/master/TUTORIAL_SF_home_price_visualization.R">we share our code</a> in an effort to get others interested in mapping with ggplot and associated packages.

Our data consists of 17,527 single family home sales in San Francisco between 2009 and 2015. The data have been cleaned and each sale has been associated with a neighborhood.

In this tutorial we’ll explore the rapid neighborhood change that has occurred in San Francisco in recent years by constructing time series plots as well as point and polygon maps.

To begin, open up a new R script, set your workspace and a couple selection options and install/load the following libraries
<div id="crayon-58b6b337e692b533623296" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b533623296-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b533623296-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b533623296-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b533623296-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b533623296-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b533623296-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b533623296-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b533623296-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b533623296-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b533623296-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b533623296-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b533623296-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b533623296-13">13</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b533623296-14">14</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b533623296-15">15</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b533623296-16">16</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b533623296-17">17</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b533623296-18">18</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b533623296-19">19</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b533623296-20">20</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b533623296-21">21</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b533623296-22">22</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b533623296-23">23</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b533623296-24">24</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b533623296-1" class="crayon-line"><span class="crayon-c"># Set a working directory on your local machine</span></div>
<div id="crayon-58b6b337e692b533623296-2" class="crayon-line crayon-striped-line"><span class="crayon-e">setwd</span><span class="crayon-sy">(</span><span class="crayon-s">""</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-3" class="crayon-line"></div>
<div id="crayon-58b6b337e692b533623296-4" class="crayon-line crayon-striped-line"><span class="crayon-c"># Turn off scientific notation</span></div>
<div id="crayon-58b6b337e692b533623296-5" class="crayon-line"><span class="crayon-e">options</span><span class="crayon-sy">(</span><span class="crayon-v">scipen</span> <span class="crayon-o">=</span> <span class="crayon-s">"999"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-6" class="crayon-line crayon-striped-line"><span class="crayon-c"># Ensure strings come in as character types</span></div>
<div id="crayon-58b6b337e692b533623296-7" class="crayon-line"><span class="crayon-e">options</span><span class="crayon-sy">(</span><span class="crayon-v">stringsAsFactors</span> <span class="crayon-o">=</span> <span class="crayon-t">FALSE</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-8" class="crayon-line crayon-striped-line"></div>
<div id="crayon-58b6b337e692b533623296-9" class="crayon-line"><span class="crayon-c"># Install packages</span></div>
<div id="crayon-58b6b337e692b533623296-10" class="crayon-line crayon-striped-line"><span class="crayon-c"># Note: you must have installed each of these packages before loading them</span></div>
<div id="crayon-58b6b337e692b533623296-11" class="crayon-line"><span class="crayon-c"># Note 2: There may be some versioning issues with ggplot &amp; ggmap. </span></div>
<div id="crayon-58b6b337e692b533623296-12" class="crayon-line crayon-striped-line"><span class="crayon-c"># Check out this stackoverflow thread http://bit.ly/2lXHRFJ </span></div>
<div id="crayon-58b6b337e692b533623296-13" class="crayon-line"><span class="crayon-r">library</span><span class="crayon-sy">(</span><span class="crayon-v">ggplot2</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-14" class="crayon-line crayon-striped-line"><span class="crayon-r">library</span><span class="crayon-sy">(</span><span class="crayon-v">ggmap</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-15" class="crayon-line"><span class="crayon-r">library</span><span class="crayon-sy">(</span><span class="crayon-v">maptools</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-16" class="crayon-line crayon-striped-line"><span class="crayon-r">library</span><span class="crayon-sy">(</span><span class="crayon-v">ggthemes</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-17" class="crayon-line"><span class="crayon-r">library</span><span class="crayon-sy">(</span><span class="crayon-v">rgeos</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-18" class="crayon-line crayon-striped-line"><span class="crayon-r">library</span><span class="crayon-sy">(</span><span class="crayon-v">broom</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-19" class="crayon-line"><span class="crayon-r">library</span><span class="crayon-sy">(</span><span class="crayon-v">dplyr</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-20" class="crayon-line crayon-striped-line"><span class="crayon-r">library</span><span class="crayon-sy">(</span><span class="crayon-v">plyr</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-21" class="crayon-line"><span class="crayon-r">library</span><span class="crayon-sy">(</span><span class="crayon-v">grid</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-22" class="crayon-line crayon-striped-line"><span class="crayon-r">library</span><span class="crayon-sy">(</span><span class="crayon-v">gridExtra</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-23" class="crayon-line"><span class="crayon-r">library</span><span class="crayon-sy">(</span><span class="crayon-v">reshape2</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b533623296-24" class="crayon-line crayon-striped-line"><span class="crayon-r">library</span><span class="crayon-sy">(</span><span class="crayon-v">scales</span><span class="crayon-sy">)</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
Next, we’re going to define two themes that will tell ggplot how to construct both maps and plots. Defining our themes up front ensures that we don’t have to repeat this code over and again for every plot we generate below.

We’ll also define some color palettes. Check out the ‘Zonum Solutions’ <a href="http://www.zonums.com/online/color_ramp/">Color Ramp Generator</a> for defining custom color ramps.

We’ll create several separate ramps depending on how many colors we are going to need for a given plot.
<code></code>
<div id="crayon-58b6b337e692b285251989" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-13">13</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-14">14</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-15">15</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-16">16</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-17">17</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-18">18</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-19">19</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-20">20</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-21">21</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-22">22</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-23">23</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-24">24</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-25">25</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-26">26</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-27">27</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-28">28</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-29">29</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-30">30</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-31">31</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-32">32</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-33">33</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-34">34</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-35">35</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-36">36</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-37">37</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-38">38</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-39">39</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-40">40</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-41">41</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-42">42</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-43">43</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-44">44</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-45">45</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-46">46</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-47">47</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-48">48</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-49">49</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b285251989-50">50</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b285251989-51">51</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b285251989-1" class="crayon-line"><span class="crayon-c"># Define one that we will use for plots</span></div>
<div id="crayon-58b6b337e692b285251989-2" class="crayon-line crayon-striped-line"><span class="crayon-v">plotTheme</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-t">function</span><span class="crayon-sy">(</span><span class="crayon-v">base_size</span> <span class="crayon-o">=</span> <span class="crayon-cn">12</span><span class="crayon-sy">)</span> <span class="crayon-sy">{</span></div>
<div id="crayon-58b6b337e692b285251989-3" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">theme</span><span class="crayon-sy">(</span></div>
<div id="crayon-58b6b337e692b285251989-4" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">text</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span> <span class="crayon-v">color</span> <span class="crayon-o">=</span> <span class="crayon-s">"black"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-5" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">plot</span><span class="crayon-sy">.</span><span class="crayon-v">title</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">size</span> <span class="crayon-o">=</span> <span class="crayon-cn">18</span><span class="crayon-sy">,</span><span class="crayon-v">colour</span> <span class="crayon-o">=</span> <span class="crayon-s">"black"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-6" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">plot</span><span class="crayon-sy">.</span><span class="crayon-v">subtitle</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">face</span><span class="crayon-o">=</span><span class="crayon-s">"italic"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-7" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">plot</span><span class="crayon-sy">.</span><span class="crayon-v">caption</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">hjust</span><span class="crayon-o">=</span><span class="crayon-cn">0</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-8" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">axis</span><span class="crayon-sy">.</span><span class="crayon-v">ticks</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-9" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">panel</span><span class="crayon-sy">.</span><span class="crayon-v">background</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-10" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">panel</span><span class="crayon-sy">.</span><span class="crayon-v">grid</span><span class="crayon-sy">.</span><span class="crayon-v">major</span> <span class="crayon-o">=</span> <span class="crayon-e">element_line</span><span class="crayon-sy">(</span><span class="crayon-s">"grey80"</span><span class="crayon-sy">,</span> <span class="crayon-v">size</span> <span class="crayon-o">=</span> <span class="crayon-cn">0.1</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-11" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">panel</span><span class="crayon-sy">.</span><span class="crayon-v">grid</span><span class="crayon-sy">.</span><span class="crayon-v">minor</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-12" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">strip</span><span class="crayon-sy">.</span><span class="crayon-v">background</span> <span class="crayon-o">=</span> <span class="crayon-e">element_rect</span><span class="crayon-sy">(</span><span class="crayon-v">fill</span> <span class="crayon-o">=</span> <span class="crayon-s">"grey80"</span><span class="crayon-sy">,</span> <span class="crayon-v">color</span> <span class="crayon-o">=</span> <span class="crayon-s">"white"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-13" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">strip</span><span class="crayon-sy">.</span><span class="crayon-v">text</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">size</span><span class="crayon-o">=</span><span class="crayon-cn">12</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-14" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">axis</span><span class="crayon-sy">.</span><span class="crayon-v">title</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">size</span><span class="crayon-o">=</span><span class="crayon-cn">8</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-15" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">axis</span><span class="crayon-sy">.</span><span class="crayon-v">text</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">size</span><span class="crayon-o">=</span><span class="crayon-cn">8</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-16" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">axis</span><span class="crayon-sy">.</span><span class="crayon-v">title</span><span class="crayon-sy">.</span><span class="crayon-v">x</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">hjust</span><span class="crayon-o">=</span><span class="crayon-cn">1</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-17" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">axis</span><span class="crayon-sy">.</span><span class="crayon-v">title</span><span class="crayon-sy">.</span><span class="crayon-v">y</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">hjust</span><span class="crayon-o">=</span><span class="crayon-cn">1</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-18" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">plot</span><span class="crayon-sy">.</span><span class="crayon-v">background</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-19" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">background</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-20" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">title</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">colour</span> <span class="crayon-o">=</span> <span class="crayon-s">"black"</span><span class="crayon-sy">,</span> <span class="crayon-v">face</span> <span class="crayon-o">=</span> <span class="crayon-s">"italic"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-21" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">text</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">colour</span> <span class="crayon-o">=</span> <span class="crayon-s">"black"</span><span class="crayon-sy">,</span> <span class="crayon-v">face</span> <span class="crayon-o">=</span> <span class="crayon-s">"italic"</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b285251989-22" class="crayon-line crayon-striped-line"><span class="crayon-sy">}</span></div>
<div id="crayon-58b6b337e692b285251989-23" class="crayon-line"></div>
<div id="crayon-58b6b337e692b285251989-24" class="crayon-line crayon-striped-line"><span class="crayon-c"># And another that we will use for maps</span></div>
<div id="crayon-58b6b337e692b285251989-25" class="crayon-line"><span class="crayon-v">mapTheme</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-t">function</span><span class="crayon-sy">(</span><span class="crayon-v">base_size</span> <span class="crayon-o">=</span> <span class="crayon-cn">12</span><span class="crayon-sy">)</span> <span class="crayon-sy">{</span></div>
<div id="crayon-58b6b337e692b285251989-26" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">theme</span><span class="crayon-sy">(</span></div>
<div id="crayon-58b6b337e692b285251989-27" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">text</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span> <span class="crayon-v">color</span> <span class="crayon-o">=</span> <span class="crayon-s">"black"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-28" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">plot</span><span class="crayon-sy">.</span><span class="crayon-v">title</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">size</span> <span class="crayon-o">=</span> <span class="crayon-cn">18</span><span class="crayon-sy">,</span><span class="crayon-v">colour</span> <span class="crayon-o">=</span> <span class="crayon-s">"black"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-29" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">plot</span><span class="crayon-sy">.</span><span class="crayon-v">subtitle</span><span class="crayon-o">=</span><span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">face</span><span class="crayon-o">=</span><span class="crayon-s">"italic"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-30" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">plot</span><span class="crayon-sy">.</span><span class="crayon-v">caption</span><span class="crayon-o">=</span><span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">hjust</span><span class="crayon-o">=</span><span class="crayon-cn">0</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-31" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">axis</span><span class="crayon-sy">.</span><span class="crayon-v">ticks</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-32" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">panel</span><span class="crayon-sy">.</span><span class="crayon-v">background</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-33" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">panel</span><span class="crayon-sy">.</span><span class="crayon-v">grid</span><span class="crayon-sy">.</span><span class="crayon-v">major</span> <span class="crayon-o">=</span> <span class="crayon-e">element_line</span><span class="crayon-sy">(</span><span class="crayon-s">"grey80"</span><span class="crayon-sy">,</span> <span class="crayon-v">size</span> <span class="crayon-o">=</span> <span class="crayon-cn">0.1</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-34" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">strip</span><span class="crayon-sy">.</span><span class="crayon-v">text</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">size</span><span class="crayon-o">=</span><span class="crayon-cn">12</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-35" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">axis</span><span class="crayon-sy">.</span><span class="crayon-v">title</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-36" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">axis</span><span class="crayon-sy">.</span><span class="crayon-v">text</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-37" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">axis</span><span class="crayon-sy">.</span><span class="crayon-v">title</span><span class="crayon-sy">.</span><span class="crayon-v">x</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-38" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">axis</span><span class="crayon-sy">.</span><span class="crayon-v">title</span><span class="crayon-sy">.</span><span class="crayon-v">y</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-39" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">panel</span><span class="crayon-sy">.</span><span class="crayon-v">grid</span><span class="crayon-sy">.</span><span class="crayon-v">minor</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-40" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">strip</span><span class="crayon-sy">.</span><span class="crayon-v">background</span> <span class="crayon-o">=</span> <span class="crayon-e">element_rect</span><span class="crayon-sy">(</span><span class="crayon-v">fill</span> <span class="crayon-o">=</span> <span class="crayon-s">"grey80"</span><span class="crayon-sy">,</span> <span class="crayon-v">color</span> <span class="crayon-o">=</span> <span class="crayon-s">"white"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-41" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">plot</span><span class="crayon-sy">.</span><span class="crayon-v">background</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-42" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">background</span> <span class="crayon-o">=</span> <span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-43" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">title</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">colour</span> <span class="crayon-o">=</span> <span class="crayon-s">"black"</span><span class="crayon-sy">,</span> <span class="crayon-v">face</span> <span class="crayon-o">=</span> <span class="crayon-s">"italic"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b285251989-44" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">text</span> <span class="crayon-o">=</span> <span class="crayon-e">element_text</span><span class="crayon-sy">(</span><span class="crayon-v">colour</span> <span class="crayon-o">=</span> <span class="crayon-s">"black"</span><span class="crayon-sy">,</span> <span class="crayon-v">face</span> <span class="crayon-o">=</span> <span class="crayon-s">"italic"</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b285251989-45" class="crayon-line"><span class="crayon-sy">}</span></div>
<div id="crayon-58b6b337e692b285251989-46" class="crayon-line crayon-striped-line"></div>
<div id="crayon-58b6b337e692b285251989-47" class="crayon-line"><span class="crayon-c"># Define some palettes</span></div>
<div id="crayon-58b6b337e692b285251989-48" class="crayon-line crayon-striped-line"><span class="crayon-v">palette_9_colors</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-s">"#0DA3A0"</span><span class="crayon-sy">,</span><span class="crayon-s">"#2999A9"</span><span class="crayon-sy">,</span><span class="crayon-s">"#458FB2"</span><span class="crayon-sy">,</span><span class="crayon-s">"#6285BB"</span><span class="crayon-sy">,</span><span class="crayon-s">"#7E7CC4"</span><span class="crayon-sy">,</span><span class="crayon-s">"#9A72CD"</span><span class="crayon-sy">,</span><span class="crayon-s">"#B768D6"</span><span class="crayon-sy">,</span><span class="crayon-s">"#D35EDF"</span><span class="crayon-sy">,</span><span class="crayon-s">"#F055E9"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b285251989-49" class="crayon-line"><span class="crayon-v">palette_8_colors</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-s">"#0DA3A0"</span><span class="crayon-sy">,</span><span class="crayon-s">"#2D97AA"</span><span class="crayon-sy">,</span><span class="crayon-s">"#4D8CB4"</span><span class="crayon-sy">,</span><span class="crayon-s">"#6E81BF"</span><span class="crayon-sy">,</span><span class="crayon-s">"#8E76C9"</span><span class="crayon-sy">,</span><span class="crayon-s">"#AF6BD4"</span><span class="crayon-sy">,</span><span class="crayon-s">"#CF60DE"</span><span class="crayon-sy">,</span><span class="crayon-s">"#F055E9"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b285251989-50" class="crayon-line crayon-striped-line"><span class="crayon-v">palette_7_colors</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-s">"#2D97AA"</span><span class="crayon-sy">,</span><span class="crayon-s">"#4D8CB4"</span><span class="crayon-sy">,</span><span class="crayon-s">"#6E81BF"</span><span class="crayon-sy">,</span><span class="crayon-s">"#8E76C9"</span><span class="crayon-sy">,</span><span class="crayon-s">"#AF6BD4"</span><span class="crayon-sy">,</span><span class="crayon-s">"#CF60DE"</span><span class="crayon-sy">,</span><span class="crayon-s">"#F055E9"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b285251989-51" class="crayon-line"><span class="crayon-v">palette_1_colors</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-s">"#0DA3A0"</span><span class="crayon-sy">)</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
Next we’ll retrieve the data. First the home price data:
<div id="crayon-58b6b337e692b184916527" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b184916527-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b184916527-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b184916527-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b184916527-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b184916527-5">5</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b184916527-1" class="crayon-line"><span class="crayon-c"># Read in a csv of home sale transactions directly from github.</span></div>
<div id="crayon-58b6b337e692b184916527-2" class="crayon-line crayon-striped-line"><span class="crayon-v">sf</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-v">read</span><span class="crayon-sy">.</span><span class="crayon-e">csv</span><span class="crayon-sy">(</span><span class="crayon-s">"https://raw.githubusercontent.com/simonkassel/Visualizing_SF_home_prices_R/master/Data/SF_home_sales_demo_data.csv"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b184916527-3" class="crayon-line"></div>
<div id="crayon-58b6b337e692b184916527-4" class="crayon-line crayon-striped-line"><span class="crayon-c"># We will need to consider Sale Year as a categorical variable so we convert it from a numeric variable to a factor</span></div>
<div id="crayon-58b6b337e692b184916527-5" class="crayon-line"><span class="crayon-v">sf</span><span class="crayon-sy">$</span><span class="crayon-v">SaleYr</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-st">as</span><span class="crayon-sy">.</span><span class="crayon-e">factor</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">$</span><span class="crayon-v">SaleYr</span><span class="crayon-sy">)</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
We’ll also download and unzip a shapefile of <a href="https://data.sfgov.org/Geographic-Locations-and-Boundaries/Realtor-Neighborhoods/5gzd-g9ns">neighborhoods in San Francisco</a>.
<div id="crayon-58b6b337e692b253688374" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b253688374-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b253688374-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b253688374-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b253688374-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b253688374-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b253688374-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b253688374-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b253688374-8">8</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b253688374-1" class="crayon-line"><span class="crayon-c"># Define the URL of the zipped shapefile</span></div>
<div id="crayon-58b6b337e692b253688374-2" class="crayon-line crayon-striped-line"><span class="crayon-v">URL</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-s">"https://github.com/simonkassel/Visualizing_SF_home_prices_R/raw/master/Data/SF_neighborhoods.zip"</span></div>
<div id="crayon-58b6b337e692b253688374-3" class="crayon-line"><span class="crayon-c"># Download the shapefile to your working directory and unzip it.</span></div>
<div id="crayon-58b6b337e692b253688374-4" class="crayon-line crayon-striped-line"><span class="crayon-v">download</span><span class="crayon-sy">.</span><span class="crayon-e">file</span><span class="crayon-sy">(</span><span class="crayon-v">URL</span><span class="crayon-sy">,</span> <span class="crayon-s">"SF_neighborhoods.zip"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b253688374-5" class="crayon-line"><span class="crayon-e">unzip</span><span class="crayon-sy">(</span><span class="crayon-s">"SF_neighborhoods.zip"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b253688374-6" class="crayon-line crayon-striped-line"><span class="crayon-c"># Read it into R as a spatial polygons data frame &amp; plot</span></div>
<div id="crayon-58b6b337e692b253688374-7" class="crayon-line"><span class="crayon-v">neighb</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">readShapePoly</span><span class="crayon-sy">(</span><span class="crayon-s">"SF_neighborhoods"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b253688374-8" class="crayon-line crayon-striped-line"><span class="crayon-e">plot</span><span class="crayon-sy">(</span><span class="crayon-v">neighb</span><span class="crayon-sy">)</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
Let’s build some plots. First off, let’s check out the distribution of home prices for the entire dataset.
<div id="crayon-58b6b337e692b317074090" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b317074090-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b317074090-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b317074090-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b317074090-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b317074090-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b317074090-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b317074090-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b317074090-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b317074090-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b317074090-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b317074090-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b317074090-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b317074090-13">13</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b317074090-1" class="crayon-line"><span class="crayon-v">home_value_hist</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ggplot</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">,</span> <span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">SalePrice</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b317074090-2" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">geom_histogram</span><span class="crayon-sy">(</span><span class="crayon-v">fill</span><span class="crayon-o">=</span><span class="crayon-v">pallete_1_colors</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b317074090-3" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">xlab</span><span class="crayon-sy">(</span><span class="crayon-s">"Sale Price($)"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span> <span class="crayon-e">ylab</span><span class="crayon-sy">(</span><span class="crayon-s">"Count"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b317074090-4" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">scale_fill_manual</span><span class="crayon-sy">(</span><span class="crayon-v">values</span><span class="crayon-o">=</span><span class="crayon-v">pallete_1_colors</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b317074090-5" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">plotTheme</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b317074090-6" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">labs</span><span class="crayon-sy">(</span><span class="crayon-v">x</span><span class="crayon-o">=</span><span class="crayon-s">"Sale Price($)"</span><span class="crayon-sy">,</span> <span class="crayon-v">y</span><span class="crayon-o">=</span><span class="crayon-s">"Count"</span><span class="crayon-sy">,</span> <span class="crayon-v">title</span><span class="crayon-o">=</span><span class="crayon-s">"Distribution of San Francisco home prices"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b317074090-7" class="crayon-line"><span class="crayon-h">       </span><span class="crayon-v">subtitle</span><span class="crayon-o">=</span><span class="crayon-s">"Nominal prices (2009 - 2015)"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b317074090-8" class="crayon-line crayon-striped-line"><span class="crayon-h">       </span><span class="crayon-v">caption</span><span class="crayon-o">=</span><span class="crayon-s">"Source: San Francisco Office of the Assessor-Recorder\n@KenSteif &amp; @SimonKassel"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b317074090-9" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">scale_x_continuous</span><span class="crayon-sy">(</span><span class="crayon-v">labels</span> <span class="crayon-o">=</span> <span class="crayon-v">comma</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span> <span class="crayon-e">scale_y_continuous</span><span class="crayon-sy">(</span><span class="crayon-v">labels</span> <span class="crayon-o">=</span> <span class="crayon-v">comma</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b317074090-10" class="crayon-line crayon-striped-line"><span class="crayon-c"># Plotting it:</span></div>
<div id="crayon-58b6b337e692b317074090-11" class="crayon-line"><span class="crayon-v">home_value_hist</span></div>
<div id="crayon-58b6b337e692b317074090-12" class="crayon-line crayon-striped-line"><span class="crayon-c"># And saving it to the working directory:</span></div>
<div id="crayon-58b6b337e692b317074090-13" class="crayon-line"><span class="crayon-e">ggsave</span><span class="crayon-sy">(</span><span class="crayon-s">"plot1_histogram.png"</span><span class="crayon-sy">,</span> <span class="crayon-v">home_value_hist</span><span class="crayon-sy">,</span> <span class="crayon-v">width</span> <span class="crayon-o">=</span> <span class="crayon-cn">8</span><span class="crayon-sy">,</span> <span class="crayon-v">height</span> <span class="crayon-o">=</span> <span class="crayon-cn">4</span><span class="crayon-sy">,</span> <span class="crayon-v">device</span> <span class="crayon-o">=</span> <span class="crayon-s">"png"</span><span class="crayon-sy">)</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
<img class="size-large wp-image-694 aligncenter" src="http://the-r.kr/wp-content/uploads/2017/03/plot1_histogram-792x396.png" alt="plot1_histogram" width="792" height="396" />

(<a href="http://i.imgur.com/hACFcCv.png">Higher resolution</a>)

It seems as though there may be some outliers. We’ll remove anything greater than 2.5 standard deviations from the mean.
<div id="crayon-58b6b337e692b588958324" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b588958324-1">1</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b588958324-1" class="crayon-line"><span class="crayon-v">sf</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-v">sf</span><span class="crayon-sy">[</span><span class="crayon-e">which</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">$</span><span class="crayon-v">SalePrice</span> <span class="crayon-o">&lt;</span> <span class="crayon-e">mean</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">$</span><span class="crayon-v">SalePrice</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span> <span class="crayon-sy">(</span><span class="crayon-cn">2.5</span> <span class="crayon-o">*</span> <span class="crayon-e">sd</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">$</span><span class="crayon-v">SalePrice</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span> <span class="crayon-sy">]</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
Next, we’ll check out the distribution of prices for each year using a violin plot.
<div id="crayon-58b6b337e692b510410280" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b510410280-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b510410280-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b510410280-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b510410280-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b510410280-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b510410280-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b510410280-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b510410280-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b510410280-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b510410280-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b510410280-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b510410280-12">12</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b510410280-1" class="crayon-line"><span class="crayon-v">home_value_violin</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ggplot</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">,</span> <span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">x</span><span class="crayon-o">=</span><span class="crayon-v">SaleYr</span><span class="crayon-sy">,</span> <span class="crayon-v">y</span><span class="crayon-o">=</span><span class="crayon-v">SalePrice</span><span class="crayon-sy">,</span> <span class="crayon-v">fill</span><span class="crayon-o">=</span><span class="crayon-v">SaleYr</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b510410280-2" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">geom_violin</span><span class="crayon-sy">(</span><span class="crayon-v">color</span> <span class="crayon-o">=</span> <span class="crayon-s">"grey50"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b510410280-3" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">xlab</span><span class="crayon-sy">(</span><span class="crayon-s">"Sale Price($)"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span> <span class="crayon-e">ylab</span><span class="crayon-sy">(</span><span class="crayon-s">"Count"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b510410280-4" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">scale_fill_manual</span><span class="crayon-sy">(</span><span class="crayon-v">values</span><span class="crayon-o">=</span><span class="crayon-v">pallete_7_colors</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b510410280-5" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">stat_summary</span><span class="crayon-sy">(</span><span class="crayon-v">fun</span><span class="crayon-sy">.</span><span class="crayon-v">y</span><span class="crayon-o">=</span><span class="crayon-v">mean</span><span class="crayon-sy">,</span> <span class="crayon-v">geom</span><span class="crayon-o">=</span><span class="crayon-s">"point"</span><span class="crayon-sy">,</span> <span class="crayon-v">size</span><span class="crayon-o">=</span><span class="crayon-cn">2</span><span class="crayon-sy">,</span> <span class="crayon-v">colour</span><span class="crayon-o">=</span><span class="crayon-s">"white"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b510410280-6" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">plotTheme</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span> <span class="crayon-e">theme</span><span class="crayon-sy">(</span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">position</span><span class="crayon-o">=</span><span class="crayon-s">"none"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b510410280-7" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">scale_y_continuous</span><span class="crayon-sy">(</span><span class="crayon-v">labels</span> <span class="crayon-o">=</span> <span class="crayon-v">comma</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b510410280-8" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">labs</span><span class="crayon-sy">(</span><span class="crayon-v">x</span><span class="crayon-o">=</span><span class="crayon-s">"Year"</span><span class="crayon-sy">,</span><span class="crayon-v">y</span><span class="crayon-o">=</span><span class="crayon-s">"Sale Price($)"</span><span class="crayon-sy">,</span><span class="crayon-v">title</span><span class="crayon-o">=</span><span class="crayon-s">"Distribution of San Francisco home prices"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b510410280-9" class="crayon-line"><span class="crayon-h">       </span><span class="crayon-v">subtitle</span><span class="crayon-o">=</span><span class="crayon-s">"Nominal prices (2009 - 2015); Sale price means visualized as points"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b510410280-10" class="crayon-line crayon-striped-line"><span class="crayon-h">       </span><span class="crayon-v">caption</span><span class="crayon-o">=</span><span class="crayon-s">"Source: San Francisco Office of the Assessor-Recorder\n@KenSteif &amp; @SimonKassel"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b510410280-11" class="crayon-line"><span class="crayon-e">home_value_violin</span></div>
<div id="crayon-58b6b337e692b510410280-12" class="crayon-line crayon-striped-line"><span class="crayon-e">ggsave</span><span class="crayon-sy">(</span><span class="crayon-s">"plot2_violin.png"</span><span class="crayon-sy">,</span> <span class="crayon-v">home_value_violin</span><span class="crayon-sy">,</span> <span class="crayon-v">width</span> <span class="crayon-o">=</span> <span class="crayon-cn">8</span><span class="crayon-sy">,</span> <span class="crayon-v">height</span> <span class="crayon-o">=</span> <span class="crayon-cn">4</span><span class="crayon-sy">,</span> <span class="crayon-v">device</span> <span class="crayon-o">=</span> <span class="crayon-s">"png"</span><span class="crayon-sy">)</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
<img class=" wp-image-698 aligncenter" src="http://the-r.kr/wp-content/uploads/2017/03/plot2_violin-792x396.png" alt="plot2_violin" width="916" height="458" />

(<a href="http://i.imgur.com/9TtLc3h.png">Higher resolution</a>)

The white circles denote sale price means for each year. Not only do prices increase over time, but by the end of the time series, there far fewer sales under the $1 million mark and many more above it.

Let’s make some maps.  Our first step is to download a basemap using the fantastic ggmap package (<a href="https://www.nceas.ucsb.edu/~frazier/RSpatialGuides/ggmap/ggmapCheatsheet.pdf">PDF</a>).  We’ll create a bounding box delineated by the neighborhood shapefile and then download the basemap.
<div id="crayon-58b6b337e692b340009272" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b340009272-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b340009272-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b340009272-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b340009272-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b340009272-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b340009272-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b340009272-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b340009272-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b340009272-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b340009272-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b340009272-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b340009272-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b340009272-13">13</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b340009272-14">14</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b340009272-15">15</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b340009272-16">16</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b340009272-1" class="crayon-line"><span class="crayon-c"># Define the bounding box</span></div>
<div id="crayon-58b6b337e692b340009272-2" class="crayon-line crayon-striped-line"><span class="crayon-v">bbox</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-v">neighb</span><span class="crayon-sy">@</span><span class="crayon-v">bbox</span></div>
<div id="crayon-58b6b337e692b340009272-3" class="crayon-line"></div>
<div id="crayon-58b6b337e692b340009272-4" class="crayon-line crayon-striped-line"><span class="crayon-c"># Manipulate these values slightly so that we get some padding on our basemap between the edge of the data and the edge of the map</span></div>
<div id="crayon-58b6b337e692b340009272-5" class="crayon-line"><span class="crayon-v">sf_bbox</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-v">left</span> <span class="crayon-o">=</span> <span class="crayon-v">bbox</span><span class="crayon-sy">[</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span> <span class="crayon-cn">1</span><span class="crayon-sy">]</span> <span class="crayon-o">-</span> <span class="crayon-sy">.</span><span class="crayon-cn">01</span><span class="crayon-sy">,</span> <span class="crayon-v">bottom</span> <span class="crayon-o">=</span> <span class="crayon-v">bbox</span><span class="crayon-sy">[</span><span class="crayon-cn">2</span><span class="crayon-sy">,</span> <span class="crayon-cn">1</span><span class="crayon-sy">]</span> <span class="crayon-o">-</span> <span class="crayon-sy">.</span><span class="crayon-cn">005</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b340009272-6" class="crayon-line crayon-striped-line"><span class="crayon-h">             </span><span class="crayon-v">right</span> <span class="crayon-o">=</span> <span class="crayon-v">bbox</span><span class="crayon-sy">[</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span> <span class="crayon-cn">2</span><span class="crayon-sy">]</span> <span class="crayon-o">+</span> <span class="crayon-sy">.</span><span class="crayon-cn">01</span><span class="crayon-sy">,</span> <span class="crayon-v">top</span> <span class="crayon-o">=</span> <span class="crayon-v">bbox</span><span class="crayon-sy">[</span><span class="crayon-cn">2</span><span class="crayon-sy">,</span> <span class="crayon-cn">2</span><span class="crayon-sy">]</span> <span class="crayon-o">+</span> <span class="crayon-sy">.</span><span class="crayon-cn">005</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b340009272-7" class="crayon-line"><span class="crayon-c"># Download the basemap</span></div>
<div id="crayon-58b6b337e692b340009272-8" class="crayon-line crayon-striped-line"><span class="crayon-v">basemap</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">get_stamenmap</span><span class="crayon-sy">(</span></div>
<div id="crayon-58b6b337e692b340009272-9" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-v">bbox</span> <span class="crayon-o">=</span> <span class="crayon-v">sf_bbox</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b340009272-10" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-v">zoom</span> <span class="crayon-o">=</span> <span class="crayon-cn">13</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b340009272-11" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-v">maptype</span> <span class="crayon-o">=</span> <span class="crayon-s">"toner-lite"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b340009272-12" class="crayon-line crayon-striped-line"></div>
<div id="crayon-58b6b337e692b340009272-13" class="crayon-line"><span class="crayon-c"># Map it</span></div>
<div id="crayon-58b6b337e692b340009272-14" class="crayon-line crayon-striped-line"><span class="crayon-v">bmMap</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ggmap</span><span class="crayon-sy">(</span><span class="crayon-v">basemap</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span> <span class="crayon-e">mapTheme</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b340009272-15" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">labs</span><span class="crayon-sy">(</span><span class="crayon-v">title</span><span class="crayon-o">=</span><span class="crayon-s">"San Francisco basemap"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b340009272-16" class="crayon-line crayon-striped-line"><span class="crayon-v">bmMap</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
<img class="aligncenter wp-image-701" src="http://the-r.kr/wp-content/uploads/2017/03/plot3_basemap-792x792.png" alt="plot3_basemap" width="456" height="456" />

Let’s put this basemap to work using it to create a <a href="https://en.wikipedia.org/wiki/Small_multiple">small multiple plot</a> of prices by year. The ‘facet’ command in ggplot (line 4 below) makes this possible. Note that here we are calling the map theme created above.
<div id="crayon-58b6b337e692b051153358" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b051153358-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b051153358-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b051153358-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b051153358-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b051153358-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b051153358-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b051153358-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b051153358-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b051153358-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b051153358-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b051153358-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b051153358-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b051153358-13">13</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b051153358-1" class="crayon-line"><span class="crayon-v">prices_mapped_by_year</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ggmap</span><span class="crayon-sy">(</span><span class="crayon-v">basemap</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b051153358-2" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">geom_point</span><span class="crayon-sy">(</span><span class="crayon-v">data</span> <span class="crayon-o">=</span> <span class="crayon-v">sf</span><span class="crayon-sy">,</span> <span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">x</span> <span class="crayon-o">=</span> <span class="crayon-t">long</span><span class="crayon-sy">,</span> <span class="crayon-v">y</span> <span class="crayon-o">=</span> <span class="crayon-v">lat</span><span class="crayon-sy">,</span> <span class="crayon-v">color</span> <span class="crayon-o">=</span> <span class="crayon-v">SalePrice</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b051153358-3" class="crayon-line"><span class="crayon-h">             </span><span class="crayon-v">size</span> <span class="crayon-o">=</span> <span class="crayon-sy">.</span><span class="crayon-cn">25</span><span class="crayon-sy">,</span> <span class="crayon-v">alpha</span> <span class="crayon-o">=</span> <span class="crayon-cn">0.6</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b051153358-4" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">facet_wrap</span><span class="crayon-sy">(</span><span class="crayon-o">~</span><span class="crayon-v">SaleYr</span><span class="crayon-sy">,</span> <span class="crayon-v">scales</span> <span class="crayon-o">=</span> <span class="crayon-s">"fixed"</span><span class="crayon-sy">,</span> <span class="crayon-v">ncol</span> <span class="crayon-o">=</span> <span class="crayon-cn">4</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b051153358-5" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">coord_map</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b051153358-6" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">mapTheme</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span> <span class="crayon-e">theme</span><span class="crayon-sy">(</span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">position</span> <span class="crayon-o">=</span> <span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-sy">.</span><span class="crayon-cn">85</span><span class="crayon-sy">,</span> <span class="crayon-sy">.</span><span class="crayon-cn">25</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b051153358-7" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">scale_color_gradientn</span><span class="crayon-sy">(</span><span class="crayon-s">"Sale Price"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b051153358-8" class="crayon-line crayon-striped-line"><span class="crayon-h">                        </span><span class="crayon-v">colors</span> <span class="crayon-o">=</span> <span class="crayon-v">pallete_8_colors</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b051153358-9" class="crayon-line"><span class="crayon-h">                        </span><span class="crayon-v">labels</span> <span class="crayon-o">=</span> <span class="crayon-v">scales</span><span class="crayon-o">::</span><span class="crayon-e">dollar_format</span><span class="crayon-sy">(</span><span class="crayon-v">prefix</span> <span class="crayon-o">=</span> <span class="crayon-s">"$"</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b051153358-10" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">labs</span><span class="crayon-sy">(</span><span class="crayon-v">title</span><span class="crayon-o">=</span><span class="crayon-s">"Distribution of San Francisco home prices"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b051153358-11" class="crayon-line"><span class="crayon-h">       </span><span class="crayon-v">subtitle</span><span class="crayon-o">=</span><span class="crayon-s">"Nominal prices (2009 - 2015)"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b051153358-12" class="crayon-line crayon-striped-line"><span class="crayon-h">       </span><span class="crayon-v">caption</span><span class="crayon-o">=</span><span class="crayon-s">"Source: San Francisco Office of the Assessor-Recorder\n@KenSteif &amp; @SimonKassel"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b051153358-13" class="crayon-line"><span class="crayon-v">prices_mapped_by_year</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
<img class="size-large wp-image-703 aligncenter" src="http://the-r.kr/wp-content/uploads/2017/03/plot4_point-map-e1487598425346-792x508.png" alt="plot4_point map" width="792" height="508" />

(<a href="http://i.imgur.com/daft5G4.png">Higher resolution</a>)

The movement of prices at $2 million and above move out across the landscape, almost with a contagion effect. By 2015, these highest priced sale abut Interstate 280 in the southern section of the city.

To see the full extent of the change, it may be easier to look only at the first and last years of the time series. Let’s use the ‘subset’ command to pull out just the first and last years.
<div id="crayon-58b6b337e692b977776880" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b977776880-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b977776880-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b977776880-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b977776880-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b977776880-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b977776880-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b977776880-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b977776880-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b977776880-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b977776880-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b977776880-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b977776880-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b977776880-13">13</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b977776880-14">14</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b977776880-15">15</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b977776880-1" class="crayon-line"><span class="crayon-i">We</span>'<span class="crayon-e">ll </span><span class="crayon-e">stack </span><span class="crayon-e">the </span><span class="crayon-e">two </span><span class="crayon-e">maps </span><span class="crayon-st">and</span> <span class="crayon-e">increase </span><span class="crayon-e">the </span><span class="crayon-e">point </span><span class="crayon-v">size</span><span class="crayon-sy">.</span></div>
<div id="crayon-58b6b337e692b977776880-2" class="crayon-line crayon-striped-line"><span class="crayon-v">prices_mapped_2009_2015</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ggmap</span><span class="crayon-sy">(</span><span class="crayon-v">basemap</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b977776880-3" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">geom_point</span><span class="crayon-sy">(</span><span class="crayon-v">data</span> <span class="crayon-o">=</span> <span class="crayon-e">subset</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">,</span> <span class="crayon-v">sf</span><span class="crayon-sy">$</span><span class="crayon-v">SaleYr</span> <span class="crayon-o">==</span> <span class="crayon-cn">2015</span> <span class="crayon-o">|</span> <span class="crayon-v">sf</span><span class="crayon-sy">$</span><span class="crayon-v">SaleYr</span> <span class="crayon-o">==</span> <span class="crayon-cn">2009</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b977776880-4" class="crayon-line crayon-striped-line"><span class="crayon-h">             </span><span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">x</span> <span class="crayon-o">=</span> <span class="crayon-t">long</span><span class="crayon-sy">,</span> <span class="crayon-v">y</span> <span class="crayon-o">=</span> <span class="crayon-v">lat</span><span class="crayon-sy">,</span> <span class="crayon-v">color</span> <span class="crayon-o">=</span> <span class="crayon-v">SalePrice</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b977776880-5" class="crayon-line"><span class="crayon-h">             </span><span class="crayon-v">size</span> <span class="crayon-o">=</span> <span class="crayon-cn">1</span><span class="crayon-sy">,</span> <span class="crayon-v">alpha</span> <span class="crayon-o">=</span> <span class="crayon-cn">0.75</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b977776880-6" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">facet_wrap</span><span class="crayon-sy">(</span><span class="crayon-o">~</span><span class="crayon-v">SaleYr</span><span class="crayon-sy">,</span> <span class="crayon-v">scales</span> <span class="crayon-o">=</span> <span class="crayon-s">"fixed"</span><span class="crayon-sy">,</span> <span class="crayon-v">ncol</span> <span class="crayon-o">=</span> <span class="crayon-cn">1</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b977776880-7" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">coord_map</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b977776880-8" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">mapTheme</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b977776880-9" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">scale_color_gradientn</span><span class="crayon-sy">(</span><span class="crayon-s">"Sale Price"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b977776880-10" class="crayon-line crayon-striped-line"><span class="crayon-h">                        </span><span class="crayon-v">colors</span> <span class="crayon-o">=</span> <span class="crayon-v">pallete_8_colors</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b977776880-11" class="crayon-line"><span class="crayon-h">                        </span><span class="crayon-v">labels</span> <span class="crayon-o">=</span> <span class="crayon-v">scales</span><span class="crayon-o">::</span><span class="crayon-e">dollar_format</span><span class="crayon-sy">(</span><span class="crayon-v">prefix</span> <span class="crayon-o">=</span> <span class="crayon-s">"$"</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b977776880-12" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">labs</span><span class="crayon-sy">(</span><span class="crayon-v">title</span><span class="crayon-o">=</span><span class="crayon-s">"Distribution of San Francisco home prices"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b977776880-13" class="crayon-line"><span class="crayon-h">       </span><span class="crayon-v">subtitle</span><span class="crayon-o">=</span><span class="crayon-s">"Nominal prices (2009 &amp; 2015)"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b977776880-14" class="crayon-line crayon-striped-line"><span class="crayon-h">       </span><span class="crayon-v">caption</span><span class="crayon-o">=</span><span class="crayon-s">"Source: San Francisco Office of the Assessor-Recorder\n@KenSteif &amp; @SimonKassel"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b977776880-15" class="crayon-line"><span class="crayon-v">prices_mapped_2009_2015</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
&nbsp;

<img class="size-large wp-image-708 aligncenter" src="http://the-r.kr/wp-content/uploads/2017/03/plot5_point-map-selected-years-792x566.png" alt="plot5_point map selected years" width="792" height="566" />

(<a href="http://i.imgur.com/o7EaYLD.png">Higher resolution</a>)

The price appreciation is readily apparent. Let’s zoom into just one neighborhood in the Mission District, where economic and cultural change are reported almost daily. First we’ll create a new data frame of just sales in the ‘Inner Mission Neighborhood’ and readjust the basemap. Then we’ll build a facetted time series map of sales.
<div id="crayon-58b6b337e692b563479725" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b563479725-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b563479725-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b563479725-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b563479725-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b563479725-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b563479725-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b563479725-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b563479725-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b563479725-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b563479725-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b563479725-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b563479725-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b563479725-13">13</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b563479725-14">14</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b563479725-15">15</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b563479725-16">16</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b563479725-17">17</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b563479725-18">18</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b563479725-19">19</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b563479725-20">20</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b563479725-21">21</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b563479725-22">22</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b563479725-23">23</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b563479725-1" class="crayon-line"><span class="crayon-c">#Subset sales for the "Inner Mission neighborhood"</span></div>
<div id="crayon-58b6b337e692b563479725-2" class="crayon-line crayon-striped-line"><span class="crayon-v">missionSales</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-v">sf</span><span class="crayon-sy">[</span><span class="crayon-e">which</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">$</span><span class="crayon-v">Neighborhood</span> <span class="crayon-o">==</span> <span class="crayon-s">"Inner Mission"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span> <span class="crayon-sy">]</span></div>
<div id="crayon-58b6b337e692b563479725-3" class="crayon-line"></div>
<div id="crayon-58b6b337e692b563479725-4" class="crayon-line crayon-striped-line"><span class="crayon-c">#Create a new basemap at the appropriate scale</span></div>
<div id="crayon-58b6b337e692b563479725-5" class="crayon-line"><span class="crayon-v">centroid_lon</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">median</span><span class="crayon-sy">(</span><span class="crayon-v">missionSales</span><span class="crayon-sy">$</span><span class="crayon-t">long</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b563479725-6" class="crayon-line crayon-striped-line"><span class="crayon-v">centroid_lat</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">median</span><span class="crayon-sy">(</span><span class="crayon-v">missionSales</span><span class="crayon-sy">$</span><span class="crayon-v">lat</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b563479725-7" class="crayon-line"><span class="crayon-v">missionBasemap</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">get_map</span><span class="crayon-sy">(</span><span class="crayon-v">location</span> <span class="crayon-o">=</span> <span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-v">lon</span> <span class="crayon-o">=</span> <span class="crayon-v">centroid_lon</span><span class="crayon-sy">,</span> <span class="crayon-v">lat</span> <span class="crayon-o">=</span> <span class="crayon-v">centroid_lat</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b563479725-8" class="crayon-line crayon-striped-line"><span class="crayon-h">                          </span><span class="crayon-r">source</span> <span class="crayon-o">=</span> <span class="crayon-s">"stamen"</span><span class="crayon-sy">,</span><span class="crayon-v">maptype</span> <span class="crayon-o">=</span> <span class="crayon-s">"toner-lite"</span><span class="crayon-sy">,</span> <span class="crayon-v">zoom</span> <span class="crayon-o">=</span> <span class="crayon-cn">15</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b563479725-9" class="crayon-line"></div>
<div id="crayon-58b6b337e692b563479725-10" class="crayon-line crayon-striped-line"><span class="crayon-c">#Create a facet map by year</span></div>
<div id="crayon-58b6b337e692b563479725-11" class="crayon-line"><span class="crayon-v">mission_mapped_by_year</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ggmap</span><span class="crayon-sy">(</span><span class="crayon-v">missionBasemap</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b563479725-12" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">geom_point</span><span class="crayon-sy">(</span><span class="crayon-v">data</span> <span class="crayon-o">=</span> <span class="crayon-v">missionSales</span><span class="crayon-sy">,</span> <span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">x</span> <span class="crayon-o">=</span> <span class="crayon-t">long</span><span class="crayon-sy">,</span> <span class="crayon-v">y</span> <span class="crayon-o">=</span> <span class="crayon-v">lat</span><span class="crayon-sy">,</span> <span class="crayon-v">color</span> <span class="crayon-o">=</span> <span class="crayon-v">SalePrice</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b563479725-13" class="crayon-line"><span class="crayon-h">             </span><span class="crayon-v">size</span> <span class="crayon-o">=</span> <span class="crayon-cn">2</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b563479725-14" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">facet_wrap</span><span class="crayon-sy">(</span><span class="crayon-o">~</span><span class="crayon-v">SaleYr</span><span class="crayon-sy">,</span> <span class="crayon-v">scales</span> <span class="crayon-o">=</span> <span class="crayon-s">"fixed"</span><span class="crayon-sy">,</span> <span class="crayon-v">ncol</span> <span class="crayon-o">=</span> <span class="crayon-cn">4</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b563479725-15" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">coord_map</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b563479725-16" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">mapTheme</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span> <span class="crayon-e">theme</span><span class="crayon-sy">(</span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">position</span> <span class="crayon-o">=</span> <span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-sy">.</span><span class="crayon-cn">85</span><span class="crayon-sy">,</span> <span class="crayon-sy">.</span><span class="crayon-cn">25</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b563479725-17" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">scale_color_gradientn</span><span class="crayon-sy">(</span><span class="crayon-s">"Sale Price"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b563479725-18" class="crayon-line crayon-striped-line"><span class="crayon-h">                        </span><span class="crayon-v">colors</span> <span class="crayon-o">=</span> <span class="crayon-v">pallete_8_colors</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b563479725-19" class="crayon-line"><span class="crayon-h">                        </span><span class="crayon-v">labels</span> <span class="crayon-o">=</span> <span class="crayon-v">scales</span><span class="crayon-o">::</span><span class="crayon-e">dollar_format</span><span class="crayon-sy">(</span><span class="crayon-v">prefix</span> <span class="crayon-o">=</span> <span class="crayon-s">"$"</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b563479725-20" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">labs</span><span class="crayon-sy">(</span><span class="crayon-v">title</span><span class="crayon-o">=</span><span class="crayon-s">"Distribution of Mission District home prices"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b563479725-21" class="crayon-line"><span class="crayon-h">       </span><span class="crayon-v">subtitle</span><span class="crayon-o">=</span><span class="crayon-s">"Nominal prices (2009 - 2015)"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b563479725-22" class="crayon-line crayon-striped-line"><span class="crayon-h">       </span><span class="crayon-v">caption</span><span class="crayon-o">=</span><span class="crayon-s">"Source: San Francisco Office of the Assessor-Recorder\n@KenSteif &amp; @SimonKassel"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b563479725-23" class="crayon-line"><span class="crayon-v">mission_mapped_by_year</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
<img class="size-large wp-image-710 aligncenter" src="http://the-r.kr/wp-content/uploads/2017/03/plot6_point-map-Mission-District-792x396.png" alt="plot6_point map Mission District" width="792" height="396" />

(<a href="http://i.imgur.com/94Okv7Z.png">Higher resolution</a>)

2015 appears to have been a watershed year for the Inner District but what about the other neighborhoods in San Francisco? To display neighborhood level trends, we’ll move from point maps to polygon maps. To begin, we need to do a bit of data wrangling – generating a new data frame with median, standard deviation, sale count, percent change and other statistics by neighborhood and time. We’ll then output our new data frame in a format suitable for mapping.
<div id="crayon-58b6b337e692b125781479" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-13">13</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-14">14</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-15">15</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-16">16</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-17">17</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-18">18</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-19">19</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-20">20</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-21">21</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-22">22</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-23">23</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-24">24</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-25">25</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-26">26</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-27">27</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-28">28</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-29">29</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-30">30</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-31">31</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-32">32</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-33">33</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-34">34</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-35">35</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-36">36</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-37">37</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-38">38</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-39">39</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-40">40</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-41">41</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-42">42</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-43">43</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-44">44</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b125781479-45">45</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b125781479-46">46</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b125781479-1" class="crayon-line"><span class="crayon-c"># We'll start by summarizing our existing sales data frame</span></div>
<div id="crayon-58b6b337e692b125781479-2" class="crayon-line crayon-striped-line"><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ddply</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">,</span> <span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-s">"Neighborhood"</span><span class="crayon-sy">,</span> <span class="crayon-s">"SaleYr"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span> <span class="crayon-v">summarise</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b125781479-3" class="crayon-line"><span class="crayon-h">                       </span><span class="crayon-v">medianPrice</span> <span class="crayon-o">=</span> <span class="crayon-e">median</span><span class="crayon-sy">(</span><span class="crayon-v">SalePrice</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b125781479-4" class="crayon-line crayon-striped-line"><span class="crayon-h">                       </span><span class="crayon-v">saleCount</span> <span class="crayon-o">=</span> <span class="crayon-e">length</span><span class="crayon-sy">(</span><span class="crayon-v">SaleYr</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b125781479-5" class="crayon-line"><span class="crayon-h">                       </span><span class="crayon-v">sdPrice</span> <span class="crayon-o">=</span> <span class="crayon-e">sd</span><span class="crayon-sy">(</span><span class="crayon-v">SalePrice</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b125781479-6" class="crayon-line crayon-striped-line"><span class="crayon-h">                       </span><span class="crayon-v">minusSd</span> <span class="crayon-o">=</span> <span class="crayon-v">medianPrice</span> <span class="crayon-o">-</span> <span class="crayon-v">sdPrice</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b125781479-7" class="crayon-line"><span class="crayon-h">                       </span><span class="crayon-v">plusSD</span> <span class="crayon-o">=</span> <span class="crayon-v">medianPrice</span> <span class="crayon-o">+</span> <span class="crayon-v">sdPrice</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b125781479-8" class="crayon-line crayon-striped-line"><span class="crayon-h">                       </span><span class="crayon-sy">.</span><span class="crayon-v">progress</span> <span class="crayon-o">=</span> <span class="crayon-s">"text"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b125781479-9" class="crayon-line"><span class="crayon-e">head</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">,</span> <span class="crayon-cn">10</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b125781479-10" class="crayon-line crayon-striped-line"></div>
<div id="crayon-58b6b337e692b125781479-11" class="crayon-line"><span class="crayon-c"># Now we'll calculate the average annual home sale count for each neighborhood</span></div>
<div id="crayon-58b6b337e692b125781479-12" class="crayon-line crayon-striped-line"><span class="crayon-v">yearly_sales</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ddply</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">,</span> <span class="crayon-o">~</span><span class="crayon-v">Neighborhood</span><span class="crayon-sy">,</span> <span class="crayon-v">summarise</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b125781479-13" class="crayon-line"><span class="crayon-h">                      </span><span class="crayon-v">avg</span><span class="crayon-sy">.</span><span class="crayon-v">yearly</span><span class="crayon-sy">.</span><span class="crayon-v">sales</span> <span class="crayon-o">=</span> <span class="crayon-e">mean</span><span class="crayon-sy">(</span><span class="crayon-v">saleCount</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b125781479-14" class="crayon-line crayon-striped-line"></div>
<div id="crayon-58b6b337e692b125781479-15" class="crayon-line"><span class="crayon-c"># Then we will use a left join to join the average sale count data frame to the original summarized data frame. </span></div>
<div id="crayon-58b6b337e692b125781479-16" class="crayon-line crayon-striped-line"><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">left_join</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">,</span> <span class="crayon-v">yearly_sales</span><span class="crayon-sy">,</span> <span class="crayon-v">by</span> <span class="crayon-o">=</span> <span class="crayon-s">"Neighborhood"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b125781479-17" class="crayon-line"></div>
<div id="crayon-58b6b337e692b125781479-18" class="crayon-line crayon-striped-line"><span class="crayon-c"># Next, we'll calculate the % change in neighborhood median home value. In order to do this we will need to reshape the data </span></div>
<div id="crayon-58b6b337e692b125781479-19" class="crayon-line"><span class="crayon-c"># again using the dcast function in the package reshape2. </span></div>
<div id="crayon-58b6b337e692b125781479-20" class="crayon-line crayon-striped-line"><span class="crayon-v">medByYear</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">dcast</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">,</span> <span class="crayon-v">Neighborhood</span> <span class="crayon-o">~</span> <span class="crayon-v">SaleYr</span><span class="crayon-sy">,</span> <span class="crayon-v">value</span><span class="crayon-sy">.</span><span class="crayon-t">var</span> <span class="crayon-o">=</span> <span class="crayon-s">"medianPrice"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b125781479-21" class="crayon-line"><span class="crayon-c"># Check out the reshaped data frame</span></div>
<div id="crayon-58b6b337e692b125781479-22" class="crayon-line crayon-striped-line"><span class="crayon-e">head</span><span class="crayon-sy">(</span><span class="crayon-v">medByYear</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b125781479-23" class="crayon-line"></div>
<div id="crayon-58b6b337e692b125781479-24" class="crayon-line crayon-striped-line"><span class="crayon-c"># We now have a data frame in which each row is a neighborhood, each column is a year and the values are the corresponding median prices. </span></div>
<div id="crayon-58b6b337e692b125781479-25" class="crayon-line"><span class="crayon-c"># Now we can easily calculate the % change from 2009 to 2015.</span></div>
<div id="crayon-58b6b337e692b125781479-26" class="crayon-line crayon-striped-line"><span class="crayon-v">medByYear</span><span class="crayon-sy">$</span><span class="crayon-v">pctChange</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-sy">(</span><span class="crayon-v">medByYear</span><span class="crayon-sy">$</span><span class="crayon-sy">`</span><span class="crayon-cn">2015</span><span class="crayon-sy">`</span> <span class="crayon-o">-</span> <span class="crayon-v">medByYear</span><span class="crayon-sy">$</span><span class="crayon-sy">`</span><span class="crayon-cn">2009</span><span class="crayon-sy">`</span><span class="crayon-sy">)</span> <span class="crayon-o">/</span> <span class="crayon-v">medByYear</span><span class="crayon-sy">$</span><span class="crayon-sy">`</span><span class="crayon-cn">2009</span><span class="crayon-sy">`</span></div>
<div id="crayon-58b6b337e692b125781479-27" class="crayon-line"><span class="crayon-c"># And join it back to our sf.summarized dataset</span></div>
<div id="crayon-58b6b337e692b125781479-28" class="crayon-line crayon-striped-line"><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">left_join</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">,</span> <span class="crayon-v">medByYear</span><span class="crayon-sy">[</span><span class="crayon-sy">,</span><span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-s">"Neighborhood"</span><span class="crayon-sy">,</span> <span class="crayon-s">"pctChange"</span><span class="crayon-sy">)</span><span class="crayon-sy">]</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b125781479-29" class="crayon-line"><span class="crayon-h">                           </span><span class="crayon-v">by</span> <span class="crayon-o">=</span> <span class="crayon-s">"Neighborhood"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b125781479-30" class="crayon-line crayon-striped-line"></div>
<div id="crayon-58b6b337e692b125781479-31" class="crayon-line"><span class="crayon-c"># Some neighborhoods have very low annual sale counts. </span></div>
<div id="crayon-58b6b337e692b125781479-32" class="crayon-line crayon-striped-line"><span class="crayon-c"># We will remove these neighborhoods from the dataset by converting them to NA.</span></div>
<div id="crayon-58b6b337e692b125781479-33" class="crayon-line"><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">$</span><span class="crayon-v">pctChange</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ifelse</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">$</span><span class="crayon-v">avg</span><span class="crayon-sy">.</span><span class="crayon-v">yearly</span><span class="crayon-sy">.</span><span class="crayon-v">sales</span> <span class="crayon-o">&lt;</span> <span class="crayon-cn">10</span><span class="crayon-sy">,</span> <span class="crayon-t ">NA</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b125781479-34" class="crayon-line crayon-striped-line"><span class="crayon-h">                                  </span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">$</span><span class="crayon-v">pctChange</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b125781479-35" class="crayon-line"></div>
<div id="crayon-58b6b337e692b125781479-36" class="crayon-line crayon-striped-line"><span class="crayon-c"># Remember the neighborhood shapefile we imported at the beginning? We must now convert it to a format that ggplot understands.</span></div>
<div id="crayon-58b6b337e692b125781479-37" class="crayon-line"><span class="crayon-v">neighb</span><span class="crayon-sy">.</span><span class="crayon-v">tidy</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">tidy</span><span class="crayon-sy">(</span><span class="crayon-v">neighb</span><span class="crayon-sy">,</span> <span class="crayon-v">region</span> <span class="crayon-o">=</span> <span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-s">'nbrhood'</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b125781479-38" class="crayon-line crayon-striped-line"><span class="crayon-c"># Look at the resulting data frame to see how it has been transformed</span></div>
<div id="crayon-58b6b337e692b125781479-39" class="crayon-line"><span class="crayon-e">head</span><span class="crayon-sy">(</span><span class="crayon-v">neighb</span><span class="crayon-sy">.</span><span class="crayon-v">tidy</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b125781479-40" class="crayon-line crayon-striped-line"></div>
<div id="crayon-58b6b337e692b125781479-41" class="crayon-line"><span class="crayon-c"># Create an identical field to 'id' but with a name that will allow us to join the data frame to our summarized price data</span></div>
<div id="crayon-58b6b337e692b125781479-42" class="crayon-line crayon-striped-line"><span class="crayon-v">neighb</span><span class="crayon-sy">.</span><span class="crayon-v">tidy</span><span class="crayon-sy">$</span><span class="crayon-v">Neighborhood</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-v">neighb</span><span class="crayon-sy">.</span><span class="crayon-v">tidy</span><span class="crayon-sy">$</span><span class="crayon-v">id</span></div>
<div id="crayon-58b6b337e692b125781479-43" class="crayon-line"></div>
<div id="crayon-58b6b337e692b125781479-44" class="crayon-line crayon-striped-line"><span class="crayon-c"># Now we're going to join these data frames together so that when we map the neighborhood polygons we can symbolize them using the summary</span></div>
<div id="crayon-58b6b337e692b125781479-45" class="crayon-line"><span class="crayon-c"># stats we created</span></div>
<div id="crayon-58b6b337e692b125781479-46" class="crayon-line crayon-striped-line"><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized_tidy</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">join</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">,</span> <span class="crayon-v">neighb</span><span class="crayon-sy">.</span><span class="crayon-v">tidy</span><span class="crayon-sy">,</span> <span class="crayon-v">by</span> <span class="crayon-o">=</span> <span class="crayon-s">"Neighborhood"</span><span class="crayon-sy">,</span> <span class="crayon-v">match</span> <span class="crayon-o">=</span> <span class="crayon-s">"all"</span><span class="crayon-sy">)</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
Now we’re ready to build some neighborhoods maps. First we’ll map median home price.
<div id="crayon-58b6b337e692b947221542" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b947221542-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b947221542-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b947221542-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b947221542-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b947221542-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b947221542-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b947221542-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b947221542-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b947221542-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b947221542-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b947221542-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b947221542-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b947221542-13">13</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b947221542-1" class="crayon-line"><span class="crayon-v">neighb_map</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ggmap</span><span class="crayon-sy">(</span><span class="crayon-v">basemap</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b947221542-2" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">geom_polygon</span><span class="crayon-sy">(</span><span class="crayon-v">data</span> <span class="crayon-o">=</span> <span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized_tidy</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b947221542-3" class="crayon-line"><span class="crayon-h">               </span><span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">x</span> <span class="crayon-o">=</span> <span class="crayon-t">long</span><span class="crayon-sy">,</span> <span class="crayon-v">y</span> <span class="crayon-o">=</span> <span class="crayon-v">lat</span><span class="crayon-sy">,</span> <span class="crayon-v">group</span> <span class="crayon-o">=</span> <span class="crayon-v">group</span><span class="crayon-sy">,</span> <span class="crayon-v">fill</span> <span class="crayon-o">=</span> <span class="crayon-v">medianPrice</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b947221542-4" class="crayon-line crayon-striped-line"><span class="crayon-h">               </span><span class="crayon-v">colour</span> <span class="crayon-o">=</span> <span class="crayon-s">"white"</span><span class="crayon-sy">,</span> <span class="crayon-v">alpha</span> <span class="crayon-o">=</span> <span class="crayon-cn">0.75</span><span class="crayon-sy">,</span> <span class="crayon-v">size</span> <span class="crayon-o">=</span> <span class="crayon-cn">0.25</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b947221542-5" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">scale_fill_gradientn</span><span class="crayon-sy">(</span><span class="crayon-s">"Neighborhood \nMedian \nSale Price"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b947221542-6" class="crayon-line crayon-striped-line"><span class="crayon-h">                       </span><span class="crayon-v">colors</span> <span class="crayon-o">=</span> <span class="crayon-v">pallete_8_colors</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b947221542-7" class="crayon-line"><span class="crayon-h">                       </span><span class="crayon-v">labels</span> <span class="crayon-o">=</span> <span class="crayon-v">scales</span><span class="crayon-o">::</span><span class="crayon-e">dollar_format</span><span class="crayon-sy">(</span><span class="crayon-v">prefix</span> <span class="crayon-o">=</span> <span class="crayon-s">"$"</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b947221542-8" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">mapTheme</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span> <span class="crayon-e">theme</span><span class="crayon-sy">(</span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">position</span> <span class="crayon-o">=</span> <span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-sy">.</span><span class="crayon-cn">85</span><span class="crayon-sy">,</span> <span class="crayon-sy">.</span><span class="crayon-cn">25</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span> <span class="crayon-e">coord_map</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b947221542-9" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">facet_wrap</span><span class="crayon-sy">(</span><span class="crayon-o">~</span><span class="crayon-v">SaleYr</span><span class="crayon-sy">,</span> <span class="crayon-v">nrow</span> <span class="crayon-o">=</span> <span class="crayon-cn">2</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b947221542-10" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">labs</span><span class="crayon-sy">(</span><span class="crayon-v">title</span><span class="crayon-o">=</span><span class="crayon-s">"Median home price by neighborhood, San Francisco "</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b947221542-11" class="crayon-line"><span class="crayon-h">       </span><span class="crayon-v">subtitle</span><span class="crayon-o">=</span><span class="crayon-s">"Nominal prices (2009 - 2015)"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b947221542-12" class="crayon-line crayon-striped-line"><span class="crayon-h">       </span><span class="crayon-v">caption</span><span class="crayon-o">=</span><span class="crayon-s">"Source: San Francisco Office of the Assessor-Recorder\n@KenSteif &amp; @SimonKassel"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b947221542-13" class="crayon-line"><span class="crayon-v">neighb_map</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
<img class="aligncenter wp-image-713 size-large" src="http://the-r.kr/wp-content/uploads/2017/03/plot7_neighborhood-home-value-e1487598386892-792x491.png" alt="plot7_neighborhood home value" width="792" height="491" />

(<a href="http://i.imgur.com/mLTE4FN.png">Higher resolution</a>)

Next we’ll map percent change in prices.
<div id="crayon-58b6b337e692b640200147" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b640200147-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b640200147-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b640200147-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b640200147-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b640200147-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b640200147-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b640200147-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b640200147-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b640200147-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b640200147-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b640200147-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b640200147-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b640200147-13">13</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b640200147-14">14</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b640200147-15">15</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b640200147-16">16</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b640200147-1" class="crayon-line"><span class="crayon-c"># Plot the percent change in neighborhood median home value over time</span></div>
<div id="crayon-58b6b337e692b640200147-2" class="crayon-line crayon-striped-line"><span class="crayon-v">change_map</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ggmap</span><span class="crayon-sy">(</span><span class="crayon-v">basemap</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b640200147-3" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">geom_polygon</span><span class="crayon-sy">(</span><span class="crayon-v">data</span> <span class="crayon-o">=</span> <span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized_tidy</span><span class="crayon-sy">[</span><span class="crayon-e">which</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized_tidy</span><span class="crayon-sy">$</span><span class="crayon-v">SaleYr</span> <span class="crayon-o">==</span> <span class="crayon-cn">2015</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span> <span class="crayon-sy">]</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b640200147-4" class="crayon-line crayon-striped-line"><span class="crayon-h">               </span><span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">x</span> <span class="crayon-o">=</span> <span class="crayon-t">long</span><span class="crayon-sy">,</span> <span class="crayon-v">y</span> <span class="crayon-o">=</span> <span class="crayon-v">lat</span><span class="crayon-sy">,</span> <span class="crayon-v">group</span> <span class="crayon-o">=</span> <span class="crayon-v">group</span><span class="crayon-sy">,</span> <span class="crayon-v">fill</span> <span class="crayon-o">=</span> <span class="crayon-v">pctChange</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b640200147-5" class="crayon-line"><span class="crayon-h">               </span><span class="crayon-v">colour</span> <span class="crayon-o">=</span> <span class="crayon-s">"white"</span><span class="crayon-sy">,</span> <span class="crayon-v">alpha</span> <span class="crayon-o">=</span> <span class="crayon-cn">0.75</span><span class="crayon-sy">,</span> <span class="crayon-v">size</span> <span class="crayon-o">=</span> <span class="crayon-cn">0.25</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b640200147-6" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">coord_map</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b640200147-7" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">scale_fill_gradientn</span><span class="crayon-sy">(</span><span class="crayon-s">"% Change"</span><span class="crayon-sy">,</span> <span class="crayon-v">colors</span> <span class="crayon-o">=</span> <span class="crayon-v">pallete_8_colors</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b640200147-8" class="crayon-line crayon-striped-line"><span class="crayon-h">                       </span><span class="crayon-v">labels</span> <span class="crayon-o">=</span> <span class="crayon-v">scales</span><span class="crayon-o">::</span><span class="crayon-e">percent_format</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b640200147-9" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">mapTheme</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b640200147-10" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">theme</span><span class="crayon-sy">(</span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">position</span> <span class="crayon-o">=</span> <span class="crayon-s">"bottom"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b640200147-11" class="crayon-line"><span class="crayon-h">        </span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">direction</span> <span class="crayon-o">=</span> <span class="crayon-s">"horizontal"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b640200147-12" class="crayon-line crayon-striped-line"><span class="crayon-h">        </span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">key</span><span class="crayon-sy">.</span><span class="crayon-v">width</span> <span class="crayon-o">=</span> <span class="crayon-e">unit</span><span class="crayon-sy">(</span><span class="crayon-sy">.</span><span class="crayon-cn">5</span><span class="crayon-sy">,</span> <span class="crayon-s">"in"</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b640200147-13" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">labs</span><span class="crayon-sy">(</span><span class="crayon-v">title</span><span class="crayon-o">=</span><span class="crayon-s">"Percent change in median home prices, San Francisco"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b640200147-14" class="crayon-line crayon-striped-line"><span class="crayon-h">       </span><span class="crayon-v">subtitle</span><span class="crayon-o">=</span><span class="crayon-s">"Nominal prices (2009 - 2015)"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b640200147-15" class="crayon-line"><span class="crayon-h">       </span><span class="crayon-v">caption</span><span class="crayon-o">=</span><span class="crayon-s">"Source: San Francisco Office of the Assessor-Recorder\nNeighborhoods with too few annual transactions are withheld\n@KenSteif &amp; @SimonKassel"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b640200147-16" class="crayon-line crayon-striped-line"><span class="crayon-v">change_map</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
<img class="size-large wp-image-715 aligncenter" src="http://the-r.kr/wp-content/uploads/2017/03/plot8_change-over-time-792x792.png" alt="plot8_change over time" width="792" height="792" />

(<a href="http://i.imgur.com/Z9kLyNt.png">Higher resolution</a>)

A picture begins to emerge when we look at percent change. It’s clear that wealthy areas around The Marina, Russian Hill and Nob Hill did not change much while areas south changed dramatically. Let’s explore the rate of change by generating some time series plots for the highest appreciating neighborhoods.

First, a bit of data wrangling.
<div id="crayon-58b6b337e692b519282263" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b519282263-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b519282263-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b519282263-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b519282263-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b519282263-5">5</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b519282263-1" class="crayon-line"><span class="crayon-c"># Lets look at the top 8 most appreciating neighborhoods.</span></div>
<div id="crayon-58b6b337e692b519282263-2" class="crayon-line crayon-striped-line"><span class="crayon-v">topPctChange</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">unique</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">$</span><span class="crayon-v">pctChange</span><span class="crayon-sy">)</span> <span class="crayon-o">%</span><span class="crayon-o">&gt;</span><span class="crayon-o">%</span> <span class="crayon-e">sort</span><span class="crayon-sy">(</span><span class="crayon-v">decreasing</span> <span class="crayon-o">=</span> <span class="crayon-t">TRUE</span><span class="crayon-sy">)</span> <span class="crayon-o">%</span><span class="crayon-o">&gt;</span><span class="crayon-o">%</span> <span class="crayon-e">head</span><span class="crayon-sy">(</span><span class="crayon-cn">8</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b519282263-3" class="crayon-line"></div>
<div id="crayon-58b6b337e692b519282263-4" class="crayon-line crayon-striped-line"><span class="crayon-c"># Well use these percentages to subset our neighborhoods data frame</span></div>
<div id="crayon-58b6b337e692b519282263-5" class="crayon-line"><span class="crayon-v">sfForTimeSeries</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">[</span><span class="crayon-e">which</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">$</span><span class="crayon-v">pctChange</span> <span class="crayon-o">%</span><span class="crayon-st">in</span><span class="crayon-o">%</span> <span class="crayon-v">topPctChange</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span> <span class="crayon-sy">]</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
Now let’s create the time series plot.
<div id="crayon-58b6b337e692b810776251" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b810776251-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b810776251-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b810776251-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b810776251-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b810776251-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b810776251-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b810776251-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b810776251-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b810776251-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b810776251-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b810776251-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b810776251-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b810776251-13">13</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b810776251-14">14</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b810776251-15">15</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b810776251-16">16</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b810776251-1" class="crayon-line"><span class="crayon-v">time</span><span class="crayon-sy">.</span><span class="crayon-v">series</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ggplot</span><span class="crayon-sy">(</span><span class="crayon-v">sfForTimeSeries</span><span class="crayon-sy">,</span> <span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">x</span> <span class="crayon-o">=</span> <span class="crayon-v">SaleYr</span><span class="crayon-sy">,</span> <span class="crayon-v">group</span><span class="crayon-o">=</span><span class="crayon-v">Neighborhood</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b810776251-2" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">geom_line</span><span class="crayon-sy">(</span><span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">y</span> <span class="crayon-o">=</span> <span class="crayon-v">medianPrice</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b810776251-3" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">geom_ribbon</span><span class="crayon-sy">(</span><span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">ymin</span> <span class="crayon-o">=</span> <span class="crayon-v">minusSd</span><span class="crayon-sy">,</span> <span class="crayon-v">ymax</span> <span class="crayon-o">=</span> <span class="crayon-v">plusSD</span><span class="crayon-sy">,</span> <span class="crayon-v">fill</span> <span class="crayon-o">=</span> <span class="crayon-v">Neighborhood</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span> <span class="crayon-v">alpha</span> <span class="crayon-o">=</span> <span class="crayon-cn">0.75</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b810776251-4" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">facet_wrap</span><span class="crayon-sy">(</span><span class="crayon-o">~</span><span class="crayon-v">Neighborhood</span><span class="crayon-sy">,</span> <span class="crayon-v">scales</span> <span class="crayon-o">=</span> <span class="crayon-s">"fixed"</span><span class="crayon-sy">,</span> <span class="crayon-v">nrow</span> <span class="crayon-o">=</span> <span class="crayon-cn">4</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b810776251-5" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">scale_y_continuous</span><span class="crayon-sy">(</span><span class="crayon-v">labels</span> <span class="crayon-o">=</span> <span class="crayon-v">scales</span><span class="crayon-o">::</span><span class="crayon-e">dollar_format</span><span class="crayon-sy">(</span><span class="crayon-v">prefix</span> <span class="crayon-o">=</span> <span class="crayon-s">"$"</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b810776251-6" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">ylab</span><span class="crayon-sy">(</span><span class="crayon-s">"Neighborhood median home price"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span> <span class="crayon-e">xlab</span><span class="crayon-sy">(</span><span class="crayon-t">NULL</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b810776251-7" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">plotTheme</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b810776251-8" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">theme</span><span class="crayon-sy">(</span></div>
<div id="crayon-58b6b337e692b810776251-9" class="crayon-line"><span class="crayon-h">    </span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">position</span> <span class="crayon-o">=</span> <span class="crayon-s">"none"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b810776251-10" class="crayon-line crayon-striped-line"><span class="crayon-h">    </span><span class="crayon-v">panel</span><span class="crayon-sy">.</span><span class="crayon-v">spacing</span><span class="crayon-sy">.</span><span class="crayon-v">y</span> <span class="crayon-o">=</span> <span class="crayon-e">unit</span><span class="crayon-sy">(</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span> <span class="crayon-s">"lines"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b810776251-11" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b810776251-12" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">scale_fill_manual</span><span class="crayon-sy">(</span><span class="crayon-v">values</span><span class="crayon-o">=</span><span class="crayon-v">pallete_8_colors</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b810776251-13" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">labs</span><span class="crayon-sy">(</span><span class="crayon-v">title</span><span class="crayon-o">=</span><span class="crayon-s">"Time series for highest growth neighborhoods, San Francisco"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b810776251-14" class="crayon-line crayon-striped-line"><span class="crayon-h">       </span><span class="crayon-v">subtitle</span><span class="crayon-o">=</span><span class="crayon-s">"Nominal prices (2009-2015); Median; Ribbon indicates 1 standard deviation"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b810776251-15" class="crayon-line"><span class="crayon-h">       </span><span class="crayon-v">caption</span><span class="crayon-o">=</span><span class="crayon-s">"Source: San Francisco Office of the Assessor-Recorder\n@KenSteif &amp; @SimonKassel"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b810776251-16" class="crayon-line crayon-striped-line"><span class="crayon-v">time</span><span class="crayon-sy">.</span><span class="crayon-v">series</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
<img class=" wp-image-716 aligncenter" src="http://the-r.kr/wp-content/uploads/2017/03/plot10_time-series-792x1056.png" alt="plot10_time series" width="565" height="753" />

(<a href="http://i.imgur.com/fOkFtsy.png">Higher resolution</a>)

This plot shows how quickly home prices appreciated in the City’s fastest changing neighborhoods. It is always helpful to add a bit of geographical context to plots like this. Next, we’ll generate a map cutout and merge it with the time series plot.

Here is the code to generate the map cutout.
<div id="crayon-58b6b337e692b934004797" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b934004797-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b934004797-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b934004797-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b934004797-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b934004797-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b934004797-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b934004797-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b934004797-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b934004797-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b934004797-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b934004797-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b934004797-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b934004797-13">13</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b934004797-14">14</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b934004797-15">15</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b934004797-1" class="crayon-line"><span class="crayon-v">sampleNeighborhoods</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ggmap</span><span class="crayon-sy">(</span><span class="crayon-v">basemap</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b934004797-2" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">geom_polygon</span><span class="crayon-sy">(</span><span class="crayon-v">data</span> <span class="crayon-o">=</span> <span class="crayon-v">neighb</span><span class="crayon-sy">.</span><span class="crayon-v">tidy</span><span class="crayon-sy">,</span> <span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">x</span> <span class="crayon-o">=</span> <span class="crayon-t">long</span><span class="crayon-sy">,</span> <span class="crayon-v">y</span> <span class="crayon-o">=</span> <span class="crayon-v">lat</span><span class="crayon-sy">,</span> <span class="crayon-v">group</span> <span class="crayon-o">=</span> <span class="crayon-v">group</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b934004797-3" class="crayon-line"><span class="crayon-h">               </span><span class="crayon-v">colour</span> <span class="crayon-o">=</span> <span class="crayon-t ">NA</span><span class="crayon-sy">,</span> <span class="crayon-v">fill</span><span class="crayon-o">=</span><span class="crayon-s">"black"</span><span class="crayon-sy">,</span> <span class="crayon-v">alpha</span> <span class="crayon-o">=</span> <span class="crayon-cn">1</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b934004797-4" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">geom_polygon</span><span class="crayon-sy">(</span><span class="crayon-v">data</span> <span class="crayon-o">=</span> <span class="crayon-v">neighb</span><span class="crayon-sy">.</span><span class="crayon-v">tidy</span><span class="crayon-sy">[</span><span class="crayon-e">which</span><span class="crayon-sy">(</span><span class="crayon-v">neighb</span><span class="crayon-sy">.</span><span class="crayon-v">tidy</span><span class="crayon-sy">$</span><span class="crayon-v">Neighborhood</span> <span class="crayon-o">%</span><span class="crayon-st">in</span><span class="crayon-o">%</span> <span class="crayon-v">sfForTimeSeries</span><span class="crayon-sy">$</span><span class="crayon-v">Neighborhood</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span> <span class="crayon-sy">]</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b934004797-5" class="crayon-line"><span class="crayon-h">               </span><span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">x</span> <span class="crayon-o">=</span> <span class="crayon-t">long</span><span class="crayon-sy">,</span> <span class="crayon-v">y</span> <span class="crayon-o">=</span> <span class="crayon-v">lat</span><span class="crayon-sy">,</span> <span class="crayon-v">group</span> <span class="crayon-o">=</span> <span class="crayon-v">group</span><span class="crayon-sy">,</span> <span class="crayon-v">fill</span> <span class="crayon-o">=</span> <span class="crayon-v">Neighborhood</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b934004797-6" class="crayon-line crayon-striped-line"><span class="crayon-h">               </span><span class="crayon-v">colour</span> <span class="crayon-o">=</span> <span class="crayon-s">"black"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b934004797-7" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">coord_map</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b934004797-8" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">scale_fill_manual</span><span class="crayon-sy">(</span><span class="crayon-v">values</span><span class="crayon-o">=</span><span class="crayon-v">pallete_9_colors</span><span class="crayon-sy">)</span><span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b934004797-9" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">mapTheme</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b934004797-10" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">theme</span><span class="crayon-sy">(</span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">position</span> <span class="crayon-o">=</span> <span class="crayon-s">"bottom"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b934004797-11" class="crayon-line"><span class="crayon-h">        </span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">direction</span> <span class="crayon-o">=</span> <span class="crayon-s">"horizontal"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b934004797-12" class="crayon-line crayon-striped-line"><span class="crayon-h">        </span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">key</span><span class="crayon-sy">.</span><span class="crayon-v">size</span> <span class="crayon-o">=</span> <span class="crayon-e">unit</span><span class="crayon-sy">(</span><span class="crayon-cn">0.15</span><span class="crayon-sy">,</span> <span class="crayon-s">"in"</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b934004797-13" class="crayon-line"><span class="crayon-h">        </span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">title</span><span class="crayon-o">=</span><span class="crayon-e">element_blank</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b934004797-14" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">guides</span><span class="crayon-sy">(</span><span class="crayon-v">fill</span><span class="crayon-o">=</span><span class="crayon-e">guide_legend</span><span class="crayon-sy">(</span><span class="crayon-v">ncol</span> <span class="crayon-o">=</span> <span class="crayon-cn">2</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b934004797-15" class="crayon-line"><span class="crayon-v">sampleNeighborhoods</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
And here is the code to merge it with the time series plot using ‘grid.arrange’.
<div id="crayon-58b6b337e692b209714614" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b209714614-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b209714614-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b209714614-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b209714614-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b209714614-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b209714614-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b209714614-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b209714614-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b209714614-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b209714614-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b209714614-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b209714614-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b209714614-13">13</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b209714614-14">14</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b209714614-15">15</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b209714614-16">16</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b209714614-1" class="crayon-line"><span class="crayon-c"># First well create a blank grob (or grid object) which will allow us to appropriately space out our plot below</span></div>
<div id="crayon-58b6b337e692b209714614-2" class="crayon-line crayon-striped-line"><span class="crayon-v">blank</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-v">grid</span><span class="crayon-sy">.</span><span class="crayon-e">rect</span><span class="crayon-sy">(</span><span class="crayon-v">gp</span><span class="crayon-o">=</span><span class="crayon-e">gpar</span><span class="crayon-sy">(</span><span class="crayon-v">col</span><span class="crayon-o">=</span><span class="crayon-s">"white"</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b209714614-3" class="crayon-line"></div>
<div id="crayon-58b6b337e692b209714614-4" class="crayon-line crayon-striped-line"><span class="crayon-c"># Next, we will create an ordered list of the plots we want to use, including 'blank' </span></div>
<div id="crayon-58b6b337e692b209714614-5" class="crayon-line"><span class="crayon-v">gs</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">list</span><span class="crayon-sy">(</span><span class="crayon-v">time</span><span class="crayon-sy">.</span><span class="crayon-v">series</span><span class="crayon-sy">,</span> <span class="crayon-v">blank</span><span class="crayon-sy">,</span> <span class="crayon-v">sampleNeighborhoods</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b209714614-6" class="crayon-line crayon-striped-line"><span class="crayon-c"># Finally, we will denote a matrix that will dictate the layout of the plots. Each number</span></div>
<div id="crayon-58b6b337e692b209714614-7" class="crayon-line"><span class="crayon-c"># in the matrix refers to a position in the list of plots.</span></div>
<div id="crayon-58b6b337e692b209714614-8" class="crayon-line crayon-striped-line"><span class="crayon-v">lay</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">rbind</span><span class="crayon-sy">(</span><span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-cn">2</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b209714614-9" class="crayon-line"><span class="crayon-h">             </span><span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-cn">2</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b209714614-10" class="crayon-line crayon-striped-line"><span class="crayon-h">             </span><span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-cn">3</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b209714614-11" class="crayon-line"><span class="crayon-h">             </span><span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-cn">3</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b209714614-12" class="crayon-line crayon-striped-line"><span class="crayon-h">             </span><span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-cn">2</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b209714614-13" class="crayon-line"><span class="crayon-h">             </span><span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-cn">1</span><span class="crayon-sy">,</span><span class="crayon-cn">2</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b209714614-14" class="crayon-line crayon-striped-line"></div>
<div id="crayon-58b6b337e692b209714614-15" class="crayon-line"><span class="crayon-c"># Arrange the plot</span></div>
<div id="crayon-58b6b337e692b209714614-16" class="crayon-line crayon-striped-line"><span class="crayon-v">grid</span><span class="crayon-sy">.</span><span class="crayon-e">arrange</span><span class="crayon-sy">(</span><span class="crayon-v">grobs</span> <span class="crayon-o">=</span> <span class="crayon-v">gs</span><span class="crayon-sy">,</span> <span class="crayon-v">layout_matrix</span> <span class="crayon-o">=</span> <span class="crayon-v">lay</span><span class="crayon-sy">)</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
<img class="size-large wp-image-719 aligncenter" src="http://the-r.kr/wp-content/uploads/2017/03/plot12_time-series-with-map-792x683.png" alt="plot12_time series with map" width="792" height="683" />

(<a href="http://i.imgur.com/LeDg71n.png">Higher resolution</a>)

Finally, is there anything more concrete that we can conclude from these data? Anecdotally, we know that San Francisco is changing. We know some neighborhoods are changing faster than others.

Typically, we would join these home sale data to external social, demographic and economic factors to explain why neighborhoods are changing so fast. As we pointed out in our <a href="http://urbanspatialanalysis.com/portfolio/predicting-gentrification-using-longitudinal-census-data/">recent piece predicting gentrification</a> however, there are a whole host of ‘endogenous’ or price-related features that are important to note when understanding neighborhood change.

Our final plot conveys one such phenomenon by plotting percent change in sale price as a function of initial, 2009 prices.
<div id="crayon-58b6b337e692b420749105" class="crayon-syntax crayon-theme-github crayon-font-monaco crayon-os-mac print-yes notranslate" data-settings=" minimize scroll-mouseover">
<div class="crayon-plain-wrap"></div>
<div class="crayon-main">
<table class="crayon-table">
<tbody>
<tr class="crayon-row">
<td class="crayon-nums " data-settings="show">
<div class="crayon-nums-content">
<div class="crayon-num" data-line="crayon-58b6b337e692b420749105-1">1</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b420749105-2">2</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b420749105-3">3</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b420749105-4">4</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b420749105-5">5</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b420749105-6">6</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b420749105-7">7</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b420749105-8">8</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b420749105-9">9</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b420749105-10">10</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b420749105-11">11</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b420749105-12">12</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b420749105-13">13</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b420749105-14">14</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b420749105-15">15</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b420749105-16">16</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b420749105-17">17</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b420749105-18">18</div>
<div class="crayon-num" data-line="crayon-58b6b337e692b420749105-19">19</div>
<div class="crayon-num crayon-striped-num" data-line="crayon-58b6b337e692b420749105-20">20</div>
</div></td>
<td class="crayon-code">
<div class="crayon-pre">
<div id="crayon-58b6b337e692b420749105-1" class="crayon-line"><span class="crayon-c"># First we create a data frame of just 2009 and remove neighborhoods </span></div>
<div id="crayon-58b6b337e692b420749105-2" class="crayon-line crayon-striped-line"><span class="crayon-c"># that have an NA value for pctChange due to on insufficient sale volume</span></div>
<div id="crayon-58b6b337e692b420749105-3" class="crayon-line"><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-cn">2009</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">[</span><span class="crayon-e">which</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-v">summarized</span><span class="crayon-sy">$</span><span class="crayon-v">SaleYr</span> <span class="crayon-o">==</span> <span class="crayon-cn">2009</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span> <span class="crayon-sy">]</span> <span class="crayon-o">%</span><span class="crayon-o">&gt;</span><span class="crayon-o">%</span> <span class="crayon-t ">na</span><span class="crayon-sy">.</span><span class="crayon-e">omit</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b420749105-4" class="crayon-line crayon-striped-line"></div>
<div id="crayon-58b6b337e692b420749105-5" class="crayon-line"><span class="crayon-c"># Then create the scatterplot using neighborhood name labels instead of points</span></div>
<div id="crayon-58b6b337e692b420749105-6" class="crayon-line crayon-striped-line"><span class="crayon-v">change_scatterplot</span> <span class="crayon-o">&lt;</span><span class="crayon-o">-</span> <span class="crayon-e">ggplot</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-cn">2009</span><span class="crayon-sy">,</span> <span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">x</span> <span class="crayon-o">=</span> <span class="crayon-v">pctChange</span><span class="crayon-sy">,</span> <span class="crayon-v">y</span> <span class="crayon-o">=</span> <span class="crayon-v">medianPrice</span><span class="crayon-sy">,</span> <span class="crayon-v">label</span> <span class="crayon-o">=</span> <span class="crayon-v">Neighborhood</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b420749105-7" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">geom_label</span><span class="crayon-sy">(</span><span class="crayon-v">data</span> <span class="crayon-o">=</span> <span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-cn">2009</span><span class="crayon-sy">[</span><span class="crayon-e">which</span><span class="crayon-sy">(</span><span class="crayon-o">!</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-cn">2009</span><span class="crayon-sy">$</span><span class="crayon-v">pctChange</span> <span class="crayon-o">%</span><span class="crayon-st">in</span><span class="crayon-o">%</span> <span class="crayon-v">topPctChange</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-sy">]</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b420749105-8" class="crayon-line crayon-striped-line"><span class="crayon-h">             </span><span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">label</span> <span class="crayon-o">=</span> <span class="crayon-v">Neighborhood</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span> <span class="crayon-v">fill</span> <span class="crayon-o">=</span> <span class="crayon-s">"grey20"</span><span class="crayon-sy">,</span> <span class="crayon-v">size</span> <span class="crayon-o">=</span> <span class="crayon-cn">2</span><span class="crayon-sy">,</span> <span class="crayon-v">color</span> <span class="crayon-o">=</span> <span class="crayon-s">"white"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b420749105-9" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">geom_label</span><span class="crayon-sy">(</span><span class="crayon-v">data</span> <span class="crayon-o">=</span> <span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-cn">2009</span><span class="crayon-sy">[</span><span class="crayon-e">which</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-cn">2009</span><span class="crayon-sy">$</span><span class="crayon-v">pctChange</span> <span class="crayon-o">%</span><span class="crayon-st">in</span><span class="crayon-o">%</span> <span class="crayon-v">topPctChange</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span><span class="crayon-sy">]</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b420749105-10" class="crayon-line crayon-striped-line"><span class="crayon-h">             </span><span class="crayon-e">aes</span><span class="crayon-sy">(</span><span class="crayon-v">label</span> <span class="crayon-o">=</span> <span class="crayon-v">Neighborhood</span><span class="crayon-sy">,</span> <span class="crayon-v">fill</span> <span class="crayon-o">=</span> <span class="crayon-v">Neighborhood</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span> <span class="crayon-v">size</span> <span class="crayon-o">=</span> <span class="crayon-cn">2</span><span class="crayon-sy">,</span> <span class="crayon-v">color</span> <span class="crayon-o">=</span> <span class="crayon-s">"white"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b420749105-11" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">scale_fill_manual</span><span class="crayon-sy">(</span><span class="crayon-v">values</span><span class="crayon-o">=</span><span class="crayon-v">pallete_9_colors</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b420749105-12" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">geom_smooth</span><span class="crayon-sy">(</span><span class="crayon-v">method</span> <span class="crayon-o">=</span> <span class="crayon-s">"lm"</span><span class="crayon-sy">,</span> <span class="crayon-v">se</span> <span class="crayon-o">=</span> <span class="crayon-t">FALSE</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b420749105-13" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">plotTheme</span><span class="crayon-sy">(</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span> <span class="crayon-e">theme</span><span class="crayon-sy">(</span><span class="crayon-v">legend</span><span class="crayon-sy">.</span><span class="crayon-v">position</span> <span class="crayon-o">=</span> <span class="crayon-s">"none"</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b420749105-14" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">scale_y_continuous</span><span class="crayon-sy">(</span><span class="crayon-v">labels</span> <span class="crayon-o">=</span> <span class="crayon-e">dollar_format</span><span class="crayon-sy">(</span><span class="crayon-v">prefix</span> <span class="crayon-o">=</span> <span class="crayon-s">"$"</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b420749105-15" class="crayon-line"><span class="crayon-h">  </span><span class="crayon-e">scale_x_continuous</span><span class="crayon-sy">(</span><span class="crayon-v">labels</span> <span class="crayon-o">=</span> <span class="crayon-v">percent</span><span class="crayon-sy">,</span> <span class="crayon-v">limits</span> <span class="crayon-o">=</span> <span class="crayon-e">c</span><span class="crayon-sy">(</span><span class="crayon-e">min</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-cn">2009</span><span class="crayon-sy">$</span><span class="crayon-v">pctChange</span> <span class="crayon-o">-</span> <span class="crayon-sy">.</span><span class="crayon-cn">04</span><span class="crayon-sy">)</span><span class="crayon-sy">,</span> <span class="crayon-e">max</span><span class="crayon-sy">(</span><span class="crayon-v">sf</span><span class="crayon-sy">.</span><span class="crayon-cn">2009</span><span class="crayon-sy">$</span><span class="crayon-v">pctChange</span> <span class="crayon-o">+</span> <span class="crayon-sy">.</span><span class="crayon-cn">025</span><span class="crayon-sy">)</span><span class="crayon-sy">)</span> <span class="crayon-sy">)</span> <span class="crayon-o">+</span></div>
<div id="crayon-58b6b337e692b420749105-16" class="crayon-line crayon-striped-line"><span class="crayon-h">  </span><span class="crayon-e">labs</span><span class="crayon-sy">(</span><span class="crayon-v">x</span><span class="crayon-o">=</span><span class="crayon-s">"% Change"</span><span class="crayon-sy">,</span> <span class="crayon-v">y</span><span class="crayon-o">=</span><span class="crayon-s">"Median Sale Price (2009)"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b420749105-17" class="crayon-line"><span class="crayon-h">       </span><span class="crayon-v">title</span><span class="crayon-o">=</span><span class="crayon-s">"Change in home price as a function of initial price"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b420749105-18" class="crayon-line crayon-striped-line"><span class="crayon-h">       </span><span class="crayon-v">subtitle</span><span class="crayon-o">=</span><span class="crayon-s">"Median price; Change between 2009 - 2015"</span><span class="crayon-sy">,</span></div>
<div id="crayon-58b6b337e692b420749105-19" class="crayon-line"><span class="crayon-h">       </span><span class="crayon-v">caption</span><span class="crayon-o">=</span><span class="crayon-s">"Source: San Francisco Office of the Assessor-Recorder\n@KenSteif &amp; @SimonKassel"</span><span class="crayon-sy">)</span></div>
<div id="crayon-58b6b337e692b420749105-20" class="crayon-line crayon-striped-line"><span class="crayon-v">change_scatterplot</span></div>
</div></td>
</tr>
</tbody>
</table>
</div>
</div>
<img class="size-large wp-image-723 aligncenter" src="http://the-r.kr/wp-content/uploads/2017/03/plot9_scatterplot-792x594.png" alt="plot9_scatterplot" width="792" height="594" />

(<a href="http://i.imgur.com/94wlMot.png">Higher resolution</a>)

This plot shows that by in large, lower priced neighborhoods in 2009 saw the greatest rates of price appreciation throughout the study period.

If you’re interested in this phenomenon, you may wish to check out the <a href="http://www.tandfonline.com/doi/abs/10.1080/01944367908977002">Rent Gap theory</a>, a now classic marxist geography explanation of gentrification first suggested by the late Neil Smith in 1979.

We hope you enjoyed this tutorial. If you want to access the entire code base in one script, you can access it via <a href="https://github.com/simonkassel/Visualizing_SF_home_prices_R/blob/master/TUTORIAL_SF_home_price_visualization.R">Simon’s GitHub page</a>.

<em>Ken Steif, PhD is the founder of Urban Spatial. He is also the director of the <a href="https://www.design.upenn.edu/interdisciplinary-programs/master-urban-spatial-analytics">Master of Urban Spatial Analytics</a> program at the University of Pennsylvania. You can follow him on Twitter <a href="https://twitter.com/kensteif">@KenSteif</a>.</em>

<em>Simon Kassel will be receiving his Masters of City Planning from the University of Pennsylvania in the Spring of 2017.  You can follow him on Twitter <a href="https://twitter.com/simonKassel">@SimonKassel</a>.</em>

&nbsp;

소스: <em><a href="http://urbanspatialanalysis.com/dataviz-tutorial-mapping-san-francisco-home-prices-using-r/">#Dataviz tutorial: Mapping San Francisco home prices using R | Urban Spatial</a></em>

&nbsp;

&nbsp;