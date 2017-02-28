---
ID: 1506
post_title: 'hrbrmstr/hrbrthemes: Opinionated, typographic-centric ggplot2 themes and theme components'
author: The-R
post_date: 2017-02-28 18:19:16
post_excerpt: ""
layout: post
permalink: >
  http://the-r.kr/2017/02/28/hrbrmstrhrbrthemes-opinionated-typographic-centric-ggplot2-themes-and-theme-components/
published: true
inline_featured_image:
  - "0"
---
<h2><code>hrbrthemes</code> : Additional Themes and Theme Components for 'ggplot2'</h2>
<a href="http://www.repostatus.org/#active"><img src="https://camo.githubusercontent.com/20bbf42586ee61bd1930ba7ae43fd8a5275852db/687474703a2f2f7777772e7265706f7374617475732e6f72672f6261646765732f302e312e302f6163746976652e737667" alt="Project Status: Active - The project has reached a stable, usable state and is being actively developed." data-canonical-src="http://www.repostatus.org/badges/0.1.0/active.svg" /></a> <a href="https://codecov.io/gh/hrbrmstr/hrbrthemes"><img src="https://camo.githubusercontent.com/d38a0e02e4504b86cc1173a2b2f06c2a2f61c4ae/68747470733a2f2f636f6465636f762e696f2f67682f687262726d7374722f687262727468656d65732f6272616e63682f6d61737465722f67726170682f62616467652e737667" alt="codecov" data-canonical-src="https://codecov.io/gh/hrbrmstr/hrbrthemes/branch/master/graph/badge.svg" /></a> <a href="https://travis-ci.org/hrbrmstr/hrbrthemes"><img src="https://camo.githubusercontent.com/fda0221c047ddd39596492a6abc784e793554e52/68747470733a2f2f7472617669732d63692e6f72672f687262726d7374722f687262727468656d65732e7376673f6272616e63683d6d6173746572" alt="Travis-CI Build Status" data-canonical-src="https://travis-ci.org/hrbrmstr/hrbrthemes.svg?branch=master" /></a> <a href="https://cran.r-project.org/package=hrbrthemes"><img src="https://camo.githubusercontent.com/b4fb8cdec4db2055533cb5134589b41265968094/687474703a2f2f7777772e722d706b672e6f72672f6261646765732f76657273696f6e2f687262727468656d6573" alt="CRAN\_Status\_Badge" data-canonical-src="http://www.r-pkg.org/badges/version/hrbrthemes" /></a> <a href="https://camo.githubusercontent.com/35fe56d7b0ad485185a0868aa00bca0f9b243b2b/687474703a2f2f6372616e6c6f67732e722d706b672e6f72672f6261646765732f6772616e642d746f74616c2f687262727468656d6573" target="_blank"><img src="https://camo.githubusercontent.com/35fe56d7b0ad485185a0868aa00bca0f9b243b2b/687474703a2f2f6372616e6c6f67732e722d706b672e6f72672f6261646765732f6772616e642d746f74616c2f687262727468656d6573" alt="downloads" data-canonical-src="http://cranlogs.r-pkg.org/badges/grand-total/hrbrthemes" /></a> <a href="https://gist.github.com/hrbrmstr/be2f2c14fd78cac24697"><img src="https://camo.githubusercontent.com/6fe89a4fe8f5ba13d2e0665069367c42f1b1fe07/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f6b6579626173652d76657269666965642d627269676874677265656e2e737667" alt="keybase verified" data-canonical-src="https://img.shields.io/badge/keybase-verified-brightgreen.svg" /></a>

<hr />

This is a very focused package that provides typography-centric themes and theme components for ggplot2. It's a an extract/riff of <a href="http://github.com/hrbrmstr/hrbrmisc"><code>hrbrmisc</code></a> created by request.

The core theme: <code>theme_ipsum</code> ("ipsum" is Latin for "precise") uses Arial Narrow which should be installed on practically any modern system, so it's "free"-ish. This font is condensed, has solid default kerning pairs and geometric numbers. That's what I consider the "font trifecta" must-have for charts. An additional quality for fonts for charts is that they have a diversity of weights. Arial Narrow (the one on most systems, anyway) does not have said diversity but this quality is not (IMO) a "must have".

The following functions are implemented/objects are exported:
<ul>
 	<li><code>theme_ipsum</code> : Arial Narrow-based theme</li>
 	<li><code>theme_ipsum_rc</code> : Roboto Condensed-based theme</li>
 	<li><code>gg_check</code>: Spell check ggplot2 plot labels</li>
 	<li><code>update_geom_font_defaults</code>: Update matching font defaults for text geoms (the default is — unsurprisingly — Arial Narrow)</li>
 	<li><code>scale_x_comma</code> / <code>scale_y_comma</code> : Comma format for axis text and <code>expand=c(0,0)</code> (you need to set limits)</li>
 	<li><code>scale_x_percent</code> / <code>scale_y_percent</code> : Percent format for axis text and <code>expand=c(0,0)</code> (you need to set limits)</li>
 	<li><code>scale_color_ipsum</code> / <code>scale_fill_ipsum</code> / <code>ipsum_pal</code> : A muted discrete color palette with 9 colors</li>
 	<li><code>font_an</code>: a short global alias for "<code>Arial Narrow</code>"</li>
 	<li><code>font_rc</code>: a short global alias for "<code>Roboto Condensed</code>"</li>
 	<li><code>font_rc_light</code>: a short global alias for "<code>Roboto Condensed Light</code>"</li>
</ul>
<h3><a id="user-content-installation" class="anchor" href="https://github.com/hrbrmstr/hrbrthemes#installation"></a>Installation</h3>
<div class="highlight highlight-source-r">
<pre><span class="pl-e">devtools</span><span class="pl-k">::</span>install_github(<span class="pl-s"><span class="pl-pds">"</span>hrbrmstr/hrbrthemes<span class="pl-pds">"</span></span>)</pre>
</div>
<h3><a id="user-content-usage" class="anchor" href="https://github.com/hrbrmstr/hrbrthemes#usage"></a>Usage</h3>
<div class="highlight highlight-source-r">
<pre>library(<span class="pl-smi">hrbrthemes</span>)
library(<span class="pl-smi">gcookbook</span>)
library(<span class="pl-smi">tidyverse</span>)

<span class="pl-c"># current verison</span>
packageVersion(<span class="pl-s"><span class="pl-pds">"</span>hrbrthemes<span class="pl-pds">"</span></span>)
<span class="pl-c">## [1] '0.1.0'</span></pre>
</div>
<h3><a id="user-content-base-theme-arial-narrow" class="anchor" href="https://github.com/hrbrmstr/hrbrthemes#base-theme-arial-narrow"></a>Base theme (Arial Narrow)</h3>
<div class="highlight highlight-source-r">
<pre>ggplot(<span class="pl-smi">mtcars</span>, aes(<span class="pl-smi">mpg</span>, <span class="pl-smi">wt</span>)) <span class="pl-k">+</span>
  geom_point() <span class="pl-k">+</span>
  labs(<span class="pl-v">x</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Fuel effiiency (mpg)<span class="pl-pds">"</span></span>, <span class="pl-v">y</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Weight (tons)<span class="pl-pds">"</span></span>,
       <span class="pl-v">title</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Seminal ggplot2 scatterplot example<span class="pl-pds">"</span></span>,
       <span class="pl-v">subtitle</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>A plot that is only useful for demonstration purposes<span class="pl-pds">"</span></span>,
       <span class="pl-v">caption</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Brought to you by the letter 'g'<span class="pl-pds">"</span></span>) <span class="pl-k">+</span> 
  theme_ipsum()</pre>
</div>
<a href="https://github.com/hrbrmstr/hrbrthemes/blob/master/README_figs/README-unnamed-chunk-5-1.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/README-unnamed-chunk-5-1.png" width="672" /></a>
<h3><a id="user-content-roboto-condensed" class="anchor" href="https://github.com/hrbrmstr/hrbrthemes#roboto-condensed"></a>Roboto Condensed</h3>
<div class="highlight highlight-source-r">
<pre>ggplot(<span class="pl-smi">mtcars</span>, aes(<span class="pl-smi">mpg</span>, <span class="pl-smi">wt</span>)) <span class="pl-k">+</span>
  geom_point() <span class="pl-k">+</span>
  labs(<span class="pl-v">x</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Fuel effiiency (mpg)<span class="pl-pds">"</span></span>, <span class="pl-v">y</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Weight (tons)<span class="pl-pds">"</span></span>,
       <span class="pl-v">title</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Seminal ggplot2 scatterplot example<span class="pl-pds">"</span></span>,
       <span class="pl-v">subtitle</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>A plot that is only useful for demonstration purposes<span class="pl-pds">"</span></span>,
       <span class="pl-v">caption</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Brought to you by the letter 'g'<span class="pl-pds">"</span></span>) <span class="pl-k">+</span> 
  theme_ipsum_rc()</pre>
</div>
<a href="https://github.com/hrbrmstr/hrbrthemes/blob/master/README_figs/README-unnamed-chunk-6-1.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/README-unnamed-chunk-6-1.png" width="672" /></a>
<h3><a id="user-content-scales-colorfill" class="anchor" href="https://github.com/hrbrmstr/hrbrthemes#scales-colorfill"></a>Scales (Color/Fill)</h3>
<div class="highlight highlight-source-r">
<pre>ggplot(<span class="pl-smi">mtcars</span>, aes(<span class="pl-smi">mpg</span>, <span class="pl-smi">wt</span>)) <span class="pl-k">+</span>
  geom_point(aes(<span class="pl-v">color</span><span class="pl-k">=</span><span class="pl-k">factor</span>(<span class="pl-smi">carb</span>))) <span class="pl-k">+</span>
  labs(<span class="pl-v">x</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Fuel effiiency (mpg)<span class="pl-pds">"</span></span>, <span class="pl-v">y</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Weight (tons)<span class="pl-pds">"</span></span>,
       <span class="pl-v">title</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Seminal ggplot2 scatterplot example<span class="pl-pds">"</span></span>,
       <span class="pl-v">subtitle</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>A plot that is only useful for demonstration purposes<span class="pl-pds">"</span></span>,
       <span class="pl-v">caption</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Brought to you by the letter 'g'<span class="pl-pds">"</span></span>) <span class="pl-k">+</span> 
  scale_color_ipsum() <span class="pl-k">+</span>
  theme_ipsum_rc()</pre>
</div>
<a href="https://github.com/hrbrmstr/hrbrthemes/blob/master/README_figs/README-unnamed-chunk-7-1.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/README-unnamed-chunk-7-1.png" width="672" /></a>
<h3><a id="user-content-scales-axis" class="anchor" href="https://github.com/hrbrmstr/hrbrthemes#scales-axis"></a>Scales (Axis)</h3>
<div class="highlight highlight-source-r">
<pre>count(<span class="pl-smi">mpg</span>, <span class="pl-smi">class</span>) %<span class="pl-k">&gt;</span>% 
  mutate(<span class="pl-v">pct</span><span class="pl-k">=</span><span class="pl-smi">n</span><span class="pl-k">/</span>sum(<span class="pl-smi">n</span>)) %<span class="pl-k">&gt;</span>% 
  ggplot(aes(<span class="pl-smi">class</span>, <span class="pl-smi">pct</span>)) <span class="pl-k">+</span>
  geom_col() <span class="pl-k">+</span>
  scale_y_percent() <span class="pl-k">+</span>
  labs(<span class="pl-v">x</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Fuel effiiency (mpg)<span class="pl-pds">"</span></span>, <span class="pl-v">y</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Weight (tons)<span class="pl-pds">"</span></span>,
       <span class="pl-v">title</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Seminal ggplot2 column chart example with percents<span class="pl-pds">"</span></span>,
       <span class="pl-v">subtitle</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>A plot that is only useful for demonstration purposes<span class="pl-pds">"</span></span>,
       <span class="pl-v">caption</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Brought to you by the letter 'g'<span class="pl-pds">"</span></span>) <span class="pl-k">+</span> 
  theme_ipsum(<span class="pl-v">grid</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Y<span class="pl-pds">"</span></span>)</pre>
</div>
<a href="https://github.com/hrbrmstr/hrbrthemes/blob/master/README_figs/README-unnamed-chunk-8-1.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/README-unnamed-chunk-8-1.png" width="672" /></a>
<div class="highlight highlight-source-r">
<pre>ggplot(<span class="pl-smi">uspopage</span>, aes(<span class="pl-v">x</span><span class="pl-k">=</span><span class="pl-smi">Year</span>, <span class="pl-v">y</span><span class="pl-k">=</span><span class="pl-smi">Thousands</span>, <span class="pl-v">fill</span><span class="pl-k">=</span><span class="pl-smi">AgeGroup</span>)) <span class="pl-k">+</span> 
  geom_area() <span class="pl-k">+</span>
  scale_fill_ipsum() <span class="pl-k">+</span>
  scale_x_continuous(<span class="pl-v">expand</span><span class="pl-k">=</span>c(<span class="pl-c1">0</span>,<span class="pl-c1">0</span>)) <span class="pl-k">+</span>
  scale_y_comma() <span class="pl-k">+</span>
  labs(<span class="pl-v">title</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Age distribution of population in the U.S., 1900-2002<span class="pl-pds">"</span></span>,
       <span class="pl-v">subtitle</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Example data from the R Graphics Cookbook<span class="pl-pds">"</span></span>,
       <span class="pl-v">caption</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Source: R Graphics Cookbook<span class="pl-pds">"</span></span>) <span class="pl-k">+</span>
  theme_ipsum_rc(<span class="pl-v">grid</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>XY<span class="pl-pds">"</span></span>) <span class="pl-k">+</span>
  theme(<span class="pl-v">axis.text.x</span><span class="pl-k">=</span>element_text(<span class="pl-v">hjust</span><span class="pl-k">=</span>c(<span class="pl-c1">0</span>, <span class="pl-c1">0.5</span>, <span class="pl-c1">0.5</span>, <span class="pl-c1">0.5</span>, <span class="pl-c1">1</span>))) <span class="pl-k">+</span>
  theme(<span class="pl-v">legend.position</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>bottom<span class="pl-pds">"</span></span>)</pre>
</div>
<a href="https://github.com/hrbrmstr/hrbrthemes/blob/master/README_figs/README-unnamed-chunk-9-1.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/README-unnamed-chunk-9-1.png" width="672" /></a>
<div class="highlight highlight-source-r">
<pre>update_geom_font_defaults(<span class="pl-smi">font_rc_light</span>)

count(<span class="pl-smi">mpg</span>, <span class="pl-smi">class</span>) %<span class="pl-k">&gt;</span>% 
  mutate(<span class="pl-v">n</span><span class="pl-k">=</span><span class="pl-smi">n</span><span class="pl-k">*</span><span class="pl-c1">2000</span>) %<span class="pl-k">&gt;</span>% 
  arrange(<span class="pl-smi">n</span>) %<span class="pl-k">&gt;</span>% 
  mutate(<span class="pl-v">class</span><span class="pl-k">=</span><span class="pl-k">factor</span>(<span class="pl-smi">class</span>, <span class="pl-v">levels</span><span class="pl-k">=</span><span class="pl-smi">class</span>)) %<span class="pl-k">&gt;</span>% 
  ggplot(aes(<span class="pl-smi">class</span>, <span class="pl-smi">n</span>)) <span class="pl-k">+</span>
  geom_col() <span class="pl-k">+</span>
  geom_text(aes(<span class="pl-v">label</span><span class="pl-k">=</span><span class="pl-e">scales</span><span class="pl-k">::</span>comma(<span class="pl-smi">n</span>)), <span class="pl-v">hjust</span><span class="pl-k">=</span><span class="pl-c1">0</span>, <span class="pl-v">nudge_y</span><span class="pl-k">=</span><span class="pl-c1">2000</span>) <span class="pl-k">+</span>
  scale_y_comma(<span class="pl-v">limits</span><span class="pl-k">=</span>c(<span class="pl-c1">0</span>,<span class="pl-c1">150000</span>)) <span class="pl-k">+</span>
  coord_flip() <span class="pl-k">+</span>
  labs(<span class="pl-v">x</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Fuel effiiency (mpg)<span class="pl-pds">"</span></span>, <span class="pl-v">y</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Weight (tons)<span class="pl-pds">"</span></span>,
       <span class="pl-v">title</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Seminal ggplot2 column chart example with commas<span class="pl-pds">"</span></span>,
       <span class="pl-v">subtitle</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>A plot that is only useful for demonstration purposes, esp since you'd never<span class="pl-cce">\n</span>really want direct labels and axis labels<span class="pl-pds">"</span></span>,
       <span class="pl-v">caption</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Brought to you by the letter 'g'<span class="pl-pds">"</span></span>) <span class="pl-k">+</span> 
  theme_ipsum_rc(<span class="pl-v">grid</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>X<span class="pl-pds">"</span></span>)</pre>
</div>
<a href="https://github.com/hrbrmstr/hrbrthemes/blob/master/README_figs/README-unnamed-chunk-10-1.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/README-unnamed-chunk-10-1.png" width="672" /></a>
<h3><a id="user-content-spellcheck-ggplot2-labels" class="anchor" href="https://github.com/hrbrmstr/hrbrthemes#spellcheck-ggplot2-labels"></a>Spellcheck ggplot2 labels</h3>
<div class="highlight highlight-source-r">
<pre><span class="pl-smi">df</span> <span class="pl-k">&lt;-</span> <span class="pl-k">data.frame</span>(<span class="pl-v">x</span><span class="pl-k">=</span>c(<span class="pl-c1">20</span>, <span class="pl-c1">25</span>, <span class="pl-c1">30</span>), <span class="pl-v">y</span><span class="pl-k">=</span>c(<span class="pl-c1">4</span>, <span class="pl-c1">4</span>, <span class="pl-c1">4</span>), <span class="pl-v">txt</span><span class="pl-k">=</span>c(<span class="pl-s"><span class="pl-pds">"</span>One<span class="pl-pds">"</span></span>, <span class="pl-s"><span class="pl-pds">"</span>Two<span class="pl-pds">"</span></span>, <span class="pl-s"><span class="pl-pds">"</span>Three<span class="pl-pds">"</span></span>))

ggplot(<span class="pl-smi">mtcars</span>, aes(<span class="pl-smi">mpg</span>, <span class="pl-smi">wt</span>)) <span class="pl-k">+</span>
  geom_point() <span class="pl-k">+</span>
  labs(<span class="pl-v">x</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>This is some txt<span class="pl-pds">"</span></span>, <span class="pl-v">y</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>This is more text<span class="pl-pds">"</span></span>,
       <span class="pl-v">title</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>Thisy is a titlle<span class="pl-pds">"</span></span>,
       <span class="pl-v">subtitle</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>This is a subtitley<span class="pl-pds">"</span></span>,
       <span class="pl-v">caption</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>This is a captien<span class="pl-pds">"</span></span>) <span class="pl-k">+</span>
  theme_ipsum_rc(<span class="pl-v">grid</span><span class="pl-k">=</span><span class="pl-s"><span class="pl-pds">"</span>XY<span class="pl-pds">"</span></span>) <span class="pl-k">-</span><span class="pl-k">&gt;</span> <span class="pl-smi">gg</span>

gg_check(<span class="pl-smi">gg</span>)
<span class="pl-c">## Possible misspelled words in [title]: (Thisy, titlle)</span>
<span class="pl-c">## Possible misspelled words in [subtitle]: (subtitley)</span>
<span class="pl-c">## Possible misspelled words in [caption]: (captien)</span></pre>
</div>
<a href="https://github.com/hrbrmstr/hrbrthemes/blob/master/README_figs/README-unnamed-chunk-11-1.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/README-unnamed-chunk-11-1.png" width="672" /></a>
<h3><a id="user-content-test-results" class="anchor" href="https://github.com/hrbrmstr/hrbrthemes#test-results"></a>Test Results</h3>
<div class="highlight highlight-source-r">
<pre>library(<span class="pl-smi">hrbrthemes</span>)
library(<span class="pl-smi">testthat</span>)

date()
<span class="pl-c">## [1] "Mon Feb 27 07:03:41 2017"</span>

test_dir(<span class="pl-s"><span class="pl-pds">"</span>tests/<span class="pl-pds">"</span></span>)
<span class="pl-c">## testthat results ========================================================================================================</span>
<span class="pl-c">## OK: 10 SKIPPED: 0 FAILED: 0</span>
<span class="pl-c">## </span>
<span class="pl-c">## DONE ===================================================================================================================</span></pre>
</div>
<h3></h3>
[embed]https://github.com/hrbrmstr/hrbrthemes[/embed]