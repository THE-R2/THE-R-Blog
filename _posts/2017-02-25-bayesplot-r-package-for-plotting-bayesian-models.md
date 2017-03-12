---
ID: 1483
post_title: '[패키지] bayesplot : 베이지안 모델 플로팅을 위한 패키지'
author: The-R
post_date: 2017-02-25 13:13:31
post_excerpt: ""
layout: post
permalink: >
  http://the-r.kr/2017/02/25/bayesplot-r-package-for-plotting-bayesian-models/
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "30"
swp_cache_timestamp:
  - "413332"
scc_share_count_google+:
  - "0"
scc_share_count_facebook:
  - "-1"
scc_share_count_pocket:
  - "0"
scc_share_count_hatebu:
  - "0"
scc_share_count_crawldate:
  - 2017/03/12 11:45:55
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
<h1>bayesplot</h1>
<a href="https://travis-ci.org/stan-dev/bayesplot"><img src="https://camo.githubusercontent.com/ac102abe9db980875268dc870dd343feabea5669/68747470733a2f2f7472617669732d63692e6f72672f7374616e2d6465762f6261796573706c6f742e7376673f6272616e63683d6d6173746572" alt="Travis-CI Build Status" data-canonical-src="https://travis-ci.org/stan-dev/bayesplot.svg?branch=master" /></a> <a href="https://codecov.io/gh/stan-dev/bayesplot"><img src="https://camo.githubusercontent.com/abf3f156e7709665a16f0df02303341a491cf09a/68747470733a2f2f636f6465636f762e696f2f67682f7374616e2d6465762f6261796573706c6f742f6272616e63682f6d61737465722f67726170682f62616467652e737667" alt="codecov" data-canonical-src="https://codecov.io/gh/stan-dev/bayesplot/branch/master/graph/badge.svg" /></a> <a href="http://cran.r-project.org/web/packages/bayesplot"><img src="https://camo.githubusercontent.com/1408e8343c37cc21667ed5d45311f051185bec90/687474703a2f2f7777772e722d706b672e6f72672f6261646765732f76657273696f6e2f6261796573706c6f743f636f6c6f723d626c7565" alt="CRAN_Status_Badge" data-canonical-src="http://www.r-pkg.org/badges/version/bayesplot?color=blue" /></a>

An R package providing a library of plotting functions for use after fitting Bayesian models (typically with MCMC). The idea is not only to provide convenient functionality for users, but also a common set of functions that can be easily used by developers working on a variety of packages for Bayesian modeling, particularly (but not necessarily) those powered by <a href="https://github.com/stan-dev/rstan"><strong>RStan</strong></a>.

베이지안 모델 (일반적으로 MCMC 포함)을 적용한 후에 사용할 플로팅 함수 라이브러리를 제공하는 R 패키지. 이 아이디어는 사용자에게 편리한 기능을 제공 할뿐만 아니라 베이 즈 모델링을위한 다양한 패키지로 작업하는 개발자가 쉽게 사용할 수있는 일반적인 기능 세트, 특히 RStan에서 제공되는 패키지 (필수는 아님)를 제공합니다.

&nbsp;

The plots created by <strong>bayesplot</strong> are ggplot objects, which means that after a plot is created it can be further customized using the various functions for modifying ggplot objects provided by the <strong>ggplot2</strong> package.
<h3><a id="user-content-installation" class="anchor" href="https://github.com/stan-dev/bayesplot#installation"></a>Installation</h3>
<ul>
 	<li>Install from CRAN:</li>
</ul>
<div class="highlight highlight-source-r">
<pre>install.packages(<span class="pl-s"><span class="pl-pds">"</span>bayesplot<span class="pl-pds">"</span></span>)</pre>
</div>
<ul>
 	<li>Install latest development version from GitHub (requires <a href="https://github.com/hadley/devtools">devtools</a> package):</li>
</ul>
<div class="highlight highlight-source-r">
<pre><span class="pl-k">if</span> (<span class="pl-k">!</span>require(<span class="pl-s"><span class="pl-pds">"</span>devtools<span class="pl-pds">"</span></span>))
  install.packages(<span class="pl-s"><span class="pl-pds">"</span>devtools<span class="pl-pds">"</span></span>)

<span class="pl-e">devtools</span><span class="pl-k">::</span>install_github(<span class="pl-s"><span class="pl-pds">"</span>stan-dev/bayesplot<span class="pl-pds">"</span></span>, <span class="pl-v">dependencies</span> <span class="pl-k">=</span> <span class="pl-c1">TRUE</span>, <span class="pl-v">build_vignettes</span> <span class="pl-k">=</span> <span class="pl-c1">TRUE</span>)</pre>
</div>
If you are not using the <a href="https://www.rstudio.com/">RStudio IDE</a> and you get an error related to "pandoc" you will either need to remove the argument <code>build_vignettes=TRUE</code> (to avoid building the vignettes) or install <a href="http://pandoc.org/">pandoc</a> (e.g., <code>brew install pandoc</code>) and probably also pandoc-citeproc (e.g., <code>brew install pandoc-citeproc</code>). If you have the <code>rmarkdown</code> R package installed then you can check if you have pandoc by running the following in R:
<div class="highlight highlight-source-r">
<pre><span class="pl-e">rmarkdown</span><span class="pl-k">::</span>pandoc_available()</pre>
</div>
<h3><a id="user-content-examples" class="anchor" href="https://github.com/stan-dev/bayesplot#examples"></a>Examples</h3>
Some quick examples using MCMC draws obtained from the <a href="https://github.com/stan-dev/rstanarm"><strong>rstanarm</strong></a> and <a href="https://github.com/stan-dev/rstan"><strong>rstan</strong></a> packages.
<div class="highlight highlight-source-r">
<pre>library(<span class="pl-s"><span class="pl-pds">"</span>bayesplot<span class="pl-pds">"</span></span>)
library(<span class="pl-s"><span class="pl-pds">"</span>rstanarm<span class="pl-pds">"</span></span>)
library(<span class="pl-s"><span class="pl-pds">"</span>ggplot2<span class="pl-pds">"</span></span>)

<span class="pl-smi">fit</span> <span class="pl-k">&lt;-</span> stan_glm(<span class="pl-smi">mpg</span> <span class="pl-k">~</span> ., <span class="pl-v">data</span> <span class="pl-k">=</span> <span class="pl-smi">mtcars</span>)
<span class="pl-smi">posterior</span> <span class="pl-k">&lt;-</span> as.matrix(<span class="pl-smi">fit</span>)

<span class="pl-smi">plot_title</span> <span class="pl-k">&lt;-</span> ggtitle(<span class="pl-s"><span class="pl-pds">"</span>Posterior distributions<span class="pl-pds">"</span></span>,
                      <span class="pl-s"><span class="pl-pds">"</span>with medians and 80% intervals<span class="pl-pds">"</span></span>)
mcmc_areas(<span class="pl-smi">posterior</span>, 
           <span class="pl-v">pars</span> <span class="pl-k">=</span> c(<span class="pl-s"><span class="pl-pds">"</span>cyl<span class="pl-pds">"</span></span>, <span class="pl-s"><span class="pl-pds">"</span>drat<span class="pl-pds">"</span></span>, <span class="pl-s"><span class="pl-pds">"</span>am<span class="pl-pds">"</span></span>, <span class="pl-s"><span class="pl-pds">"</span>wt<span class="pl-pds">"</span></span>), 
           <span class="pl-v">prob</span> <span class="pl-k">=</span> <span class="pl-c1">0.8</span>) <span class="pl-k">+</span> <span class="pl-smi">plot_title</span></pre>
</div>
<a href="https://github.com/stan-dev/bayesplot/blob/master/images/mcmc_areas-rstanarm.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/mcmc_areas-rstanarm.png" width="50%" /></a>
<div class="highlight highlight-source-r">
<pre>color_scheme_set(<span class="pl-s"><span class="pl-pds">"</span>red<span class="pl-pds">"</span></span>)
ppc_dens_overlay(<span class="pl-v">y</span> <span class="pl-k">=</span> <span class="pl-smi">fit</span><span class="pl-k">$</span><span class="pl-smi">y</span>, 
                 <span class="pl-v">yrep</span> <span class="pl-k">=</span> posterior_predict(<span class="pl-smi">fit</span>, <span class="pl-v">draws</span> <span class="pl-k">=</span> <span class="pl-c1">50</span>))</pre>
</div>
<a href="https://github.com/stan-dev/bayesplot/blob/master/images/ppc_dens_overlay-rstanarm.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/ppc_dens_overlay-rstanarm.png" width="50%" /></a>
<div class="highlight highlight-source-r">
<pre><span class="pl-c"># also works nicely with piping</span>
library(<span class="pl-s"><span class="pl-pds">"</span>dplyr<span class="pl-pds">"</span></span>)
color_scheme_set(<span class="pl-s"><span class="pl-pds">"</span>brightblue<span class="pl-pds">"</span></span>)
<span class="pl-smi">fit</span> %<span class="pl-k">&gt;</span>% 
  posterior_predict(<span class="pl-v">draws</span> <span class="pl-k">=</span> <span class="pl-c1">500</span>) %<span class="pl-k">&gt;</span>%
  ppc_stat_grouped(<span class="pl-v">y</span> <span class="pl-k">=</span> <span class="pl-smi">mtcars</span><span class="pl-k">$</span><span class="pl-smi">mpg</span>, 
                   <span class="pl-v">group</span> <span class="pl-k">=</span> <span class="pl-smi">mtcars</span><span class="pl-k">$</span><span class="pl-smi">carb</span>, 
                   <span class="pl-v">stat</span> <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">"</span>median<span class="pl-pds">"</span></span>)
</pre>
</div>
<a href="https://github.com/stan-dev/bayesplot/blob/master/images/ppc_stat_grouped-rstanarm.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/ppc_stat_grouped-rstanarm.png" width="50%" /></a>
<div class="highlight highlight-source-r">
<pre><span class="pl-c"># with rstan demo model</span>
library(<span class="pl-s"><span class="pl-pds">"</span>rstan<span class="pl-pds">"</span></span>)
<span class="pl-smi">fit2</span> <span class="pl-k">&lt;-</span> stan_demo(<span class="pl-s"><span class="pl-pds">"</span>eight_schools<span class="pl-pds">"</span></span>, <span class="pl-v">warmup</span> <span class="pl-k">=</span> <span class="pl-c1">300</span>, <span class="pl-v">iter</span> <span class="pl-k">=</span> <span class="pl-c1">700</span>)
<span class="pl-smi">posterior2</span> <span class="pl-k">&lt;-</span> extract(<span class="pl-smi">fit2</span>, <span class="pl-v">inc_warmup</span> <span class="pl-k">=</span> <span class="pl-c1">TRUE</span>, <span class="pl-v">permuted</span> <span class="pl-k">=</span> <span class="pl-c1">FALSE</span>)

color_scheme_set(<span class="pl-s"><span class="pl-pds">"</span>mix-blue-pink<span class="pl-pds">"</span></span>)
<span class="pl-smi">p</span> <span class="pl-k">&lt;-</span> mcmc_trace(<span class="pl-smi">posterior2</span>,  <span class="pl-v">pars</span> <span class="pl-k">=</span> c(<span class="pl-s"><span class="pl-pds">"</span>mu<span class="pl-pds">"</span></span>, <span class="pl-s"><span class="pl-pds">"</span>tau<span class="pl-pds">"</span></span>), <span class="pl-v">n_warmup</span> <span class="pl-k">=</span> <span class="pl-c1">300</span>,
                <span class="pl-v">facet_args</span> <span class="pl-k">=</span> <span class="pl-k">list</span>(<span class="pl-v">nrow</span> <span class="pl-k">=</span> <span class="pl-c1">2</span>, <span class="pl-v">labeller</span> <span class="pl-k">=</span> <span class="pl-smi">label_parsed</span>))
<span class="pl-smi">p</span> <span class="pl-k">+</span> facet_text(<span class="pl-v">size</span> <span class="pl-k">=</span> <span class="pl-c1">15</span>)</pre>
</div>
<a href="https://github.com/stan-dev/bayesplot/blob/master/images/mcmc_trace-rstan.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/mcmc_trace-rstan.png" width="50%" /></a>
<div class="highlight highlight-source-r">
<pre>color_scheme_set(<span class="pl-s"><span class="pl-pds">"</span>red<span class="pl-pds">"</span></span>)
<span class="pl-smi">np</span> <span class="pl-k">&lt;-</span> nuts_params(<span class="pl-smi">fit2</span>)
mcmc_nuts_energy(<span class="pl-smi">np</span>, <span class="pl-v">merge_chains</span> <span class="pl-k">=</span> <span class="pl-c1">FALSE</span>) <span class="pl-k">+</span> ggtitle(<span class="pl-s"><span class="pl-pds">"</span>NUTS Energy Diagnostic<span class="pl-pds">"</span></span>)</pre>
</div>
<a href="https://github.com/stan-dev/bayesplot/blob/master/images/mcmc_nuts_energy-rstan.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/mcmc_nuts_energy-rstan.png" width="50%" /></a>
<div class="highlight highlight-source-r">
<pre><span class="pl-c"># another example with rstanarm</span>
color_scheme_set(<span class="pl-s"><span class="pl-pds">"</span>purple<span class="pl-pds">"</span></span>)

<span class="pl-smi">fit</span> <span class="pl-k">&lt;-</span> stan_glmer(<span class="pl-smi">mpg</span> <span class="pl-k">~</span> <span class="pl-smi">wt</span> <span class="pl-k">+</span> (<span class="pl-c1">1</span><span class="pl-k">|</span><span class="pl-smi">cyl</span>), <span class="pl-v">data</span> <span class="pl-k">=</span> <span class="pl-smi">mtcars</span>)
ppc_intervals(
  <span class="pl-v">y</span> <span class="pl-k">=</span> <span class="pl-smi">mtcars</span><span class="pl-k">$</span><span class="pl-smi">mpg</span>,
  <span class="pl-v">yrep</span> <span class="pl-k">=</span> posterior_predict(<span class="pl-smi">fit</span>),
  <span class="pl-v">x</span> <span class="pl-k">=</span> <span class="pl-smi">mtcars</span><span class="pl-k">$</span><span class="pl-smi">wt</span>,
  <span class="pl-v">prob</span> <span class="pl-k">=</span> <span class="pl-c1">0.5</span>
) <span class="pl-k">+</span>
  labs(
    <span class="pl-v">x</span> <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">"</span>Weight (1000 lbs)<span class="pl-pds">"</span></span>,
    <span class="pl-v">y</span> <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">"</span>MPG<span class="pl-pds">"</span></span>,
    <span class="pl-v">title</span> <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">"</span>50% posterior predictive intervals <span class="pl-cce">\n</span>vs observed miles per gallon<span class="pl-pds">"</span></span>,
    <span class="pl-v">subtitle</span> <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">"</span>by vehicle weight<span class="pl-pds">"</span></span>
  ) <span class="pl-k">+</span>
  panel_bg(<span class="pl-v">fill</span> <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">"</span>gray95<span class="pl-pds">"</span></span>, <span class="pl-v">color</span> <span class="pl-k">=</span> <span class="pl-c1">NA</span>) <span class="pl-k">+</span>
  grid_lines(<span class="pl-v">color</span> <span class="pl-k">=</span> <span class="pl-s"><span class="pl-pds">"</span>white<span class="pl-pds">"</span></span>)</pre>
</div>
<a href="https://github.com/stan-dev/bayesplot/blob/master/images/ppc_intervals-rstanarm.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/ppc_intervals-rstanarm.png" width="55%" /></a>

&nbsp;

&nbsp;

[embed]https://github.com/stan-dev/bayesplot[/embed]