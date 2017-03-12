---
ID: 1478
post_title: '[패키지] shinystan R 패키지와 ShinyStan GUI'
author: The-R
post_date: 2017-02-25 13:09:29
post_excerpt: ""
layout: post
permalink: >
  http://the-r.kr/2017/02/25/shinystan-r-package-and-shinystan-gui/
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "14"
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
  - 2017/03/12 11:45:56
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
<h1>ShinyStan</h1>
<a href="https://travis-ci.org/stan-dev/shinystan"><img src="https://camo.githubusercontent.com/c21b59eff3cfac9a6727bd8ca0af210bbcab69a6/68747470733a2f2f7472617669732d63692e6f72672f7374616e2d6465762f7368696e797374616e2e7376673f6272616e63683d646576656c6f70" alt="Travis-CI Build Status" data-canonical-src="https://travis-ci.org/stan-dev/shinystan.svg?branch=develop" /></a> <a href="https://codecov.io/gh/stan-dev/shinystan"><img src="https://camo.githubusercontent.com/747cecec988424ffcd7fab195dd08e398b0c9b8f/687474703a2f2f636f6465636f762e696f2f67682f7374616e2d6465762f7368696e797374616e2f6272616e63682f6d61737465722f67726170682f62616467652e737667" alt="Codecov" data-canonical-src="http://codecov.io/gh/stan-dev/shinystan/branch/master/graph/badge.svg" /></a> <a href="http://cran.r-project.org/web/packages/shinystan"><img src="https://camo.githubusercontent.com/98bb930c1516994322bae82be9bbc03e01e35c4e/687474703a2f2f7777772e722d706b672e6f72672f6261646765732f76657273696f6e2f7368696e797374616e3f636f6c6f723d626c7565" alt="CRAN_Status_Badge" data-canonical-src="http://www.r-pkg.org/badges/version/shinystan?color=blue" /></a> <a href="http://cran.rstudio.com/package=shinystan"><img src="https://camo.githubusercontent.com/2d827b775570d17722d39583369b1b20b996e294/687474703a2f2f6372616e6c6f67732e722d706b672e6f72672f6261646765732f6772616e642d746f74616c2f7368696e797374616e3f636f6c6f723d626c7565" alt="RStudio CRAN Mirror Downloads" data-canonical-src="http://cranlogs.r-pkg.org/badges/grand-total/shinystan?color=blue" /></a>

ShinyStan provides immediate, informative, customizable visual and numerical summaries of model parameters and convergence diagnostics for MCMC simulations. The ShinyStan interface is coded primarily in R using the <a href="http://shiny.rstudio.com/">Shiny</a> web application framework and is available via the <strong>shinystan</strong> R package.

ShinyStan은 모델 매개 변수 및 MCMC 시뮬레이션을위한 컨버전스 진단에 대한 즉각적이고 유익한 사용자 정의 가능한 시각 및 수치 요약을 제공합니다. ShinyStan 인터페이스는 Shiny 웹 어플리케이션 프레임 워크를 사용하여 주로 R로 코딩되며 shinystan R 패키지를 통해 사용할 수 있습니다.

&nbsp;
<h3><a id="user-content-installation" class="anchor" href="https://github.com/stan-dev/shinystan#installation"></a>Installation</h3>
<ul>
 	<li>Install from CRAN:</li>
</ul>
<div class="highlight highlight-source-r">
<pre>install.packages(<span class="pl-s"><span class="pl-pds">"</span>shinystan<span class="pl-pds">"</span></span>)</pre>
</div>
If this fails, try adding the arguments <code>type='source'</code> and/or <code>repos='http://cran.rstudio.com'</code>.
<ul>
 	<li>Install from GitHub (requires <a href="https://github.com/hadley/devtools">devtools</a> package):</li>
</ul>
<div class="highlight highlight-source-r">
<pre><span class="pl-k">if</span> (<span class="pl-k">!</span>require(<span class="pl-s"><span class="pl-pds">"</span>devtools<span class="pl-pds">"</span></span>))
  install.packages(<span class="pl-s"><span class="pl-pds">"</span>devtools<span class="pl-pds">"</span></span>)
<span class="pl-e">devtools</span><span class="pl-k">::</span>install_github(<span class="pl-s"><span class="pl-pds">"</span>stan-dev/shinystan<span class="pl-pds">"</span></span>, <span class="pl-v">build_vignettes</span> <span class="pl-k">=</span> <span class="pl-c1">TRUE</span>)</pre>
</div>
<h3><a id="user-content-demo" class="anchor" href="https://github.com/stan-dev/shinystan#demo"></a>Demo</h3>
After installing run
<div class="highlight highlight-source-r">
<pre>library(<span class="pl-s"><span class="pl-pds">"</span>shinystan<span class="pl-pds">"</span></span>)
launch_shinystan_demo()</pre>
</div>
<h3><a id="user-content-screenshots" class="anchor" href="https://github.com/stan-dev/shinystan#screenshots"></a>Screenshots</h3>
<h2><a href="https://github.com/stan-dev/shinystan/blob/develop/images/home.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/home.png" width="40%" /></a></h2>
<a href="https://github.com/stan-dev/shinystan/blob/develop/images/explore.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/explore.png" width="25%" /></a><a href="https://github.com/stan-dev/shinystan/blob/develop/images/diagnose.png" target="_blank"><img src="http://the-r.kr/wp-content/uploads/2017/02/diagnose.png" width="25%" /></a>
<h3><a id="user-content-about-shinystan" class="anchor" href="https://github.com/stan-dev/shinystan#about-shinystan"></a>About ShinyStan</h3>
Applied Bayesian data analysis is primarily implemented through the MCMC algorithms offered by various software packages. When analyzing a posterior sample obtained by one of these algorithms the first step is to check for signs that the chains have converged to the target distribution and and also for signs that the algorithm might require tuning or might be ill-suited for the given model. There may also be theoretical problems or practical inefficiencies with the specification of the model.

ShinyStan provides interactive plots and tables helpful for analyzing a posterior sample, with particular attention to identifying potential problems with the performance of the MCMC algorithm or the specification of the model. ShinyStan is powered by RStudio's Shiny web application framework and works with the output of MCMC programs written in any programming language (and has extended functionality for models fit using <a href="http://mc-stan.org/interfaces/rstan.html">RStan</a> and the No-U-Turn sampler).
<h4><a id="user-content-saving-and-deploying-sharing" class="anchor" href="https://github.com/stan-dev/shinystan#saving-and-deploying-sharing"></a>Saving and deploying (sharing)</h4>
The <strong>shinystan</strong> package allows you to store the basic components of an entire project (code, posterior samples, graphs, tables, notes) in a single object. Users can save many of the plots as ggplot2 objects for further customization and easy integration in reports or post-processing for publication.

<strong>shinystan</strong> also provides the <code>deploy_shinystan</code> function, which lets you easily deploy your own ShinyStan apps online using RStudio's <a href="https://www.shinyapps.io/">ShinyApps</a> service for any of your models. Each of your apps (each of your models) will have a unique url and is compatible with Safari, Firefox, Chrome, and most other browsers.
<h4><a id="user-content-get-help-or-submit-bug-report" class="anchor" href="https://github.com/stan-dev/shinystan#get-help-or-submit-bug-report"></a>Get help or submit bug report</h4>
<ul>
 	<li><a href="https://groups.google.com/forum/#!forum/stan-users">Stan Users Google group</a></li>
 	<li><a href="https://github.com/stan-dev/shinystan/issues">ShinyStan issue tracker</a></li>
</ul>
<h4><a id="user-content-licensing" class="anchor" href="https://github.com/stan-dev/shinystan#licensing"></a>Licensing</h4>
The <strong>shinystan</strong> R package and ShinyStan interface are open source licensed under the GNU Public License, version 3 (GPLv3).

[embed]https://github.com/stan-dev/shinystan[/embed]