---
ID: 1152
post_title: '직접 코딩하며 R을 배워보자: swirl'
author: The-R
post_date: 2017-02-02 10:24:41
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/02/02/%ec%a7%81%ec%a0%91-%ec%bd%94%eb%94%a9%ed%95%98%eb%a9%b0-r%ec%9d%84-%eb%b0%b0%ec%9b%8c%eb%b3%b4%ec%9e%90-swirl/'
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "3"
slide_template:
  - default
fusion_builder_status:
  - ""
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
sbg_selected_sidebar:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_replacement:
  - 'a:1:{i:0;s:0:"";}'
sbg_selected_sidebar_2:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_2_replacement:
  - 'a:1:{i:0;s:0:"";}'
---
초보자가 R을 배울때 여러가지 강의를 듣거나 책을 구입하여 공부를 하지만 그래도 자기손으로 직접 코딩을 해보면서 배우는 방법이 실력을 쌓기에 제일 좋은 방안 입니다.

출처: <em><a href="http://swirlstats.com/">swirl: Learn R, in R.</a></em>

The swirl R package makes it fun and easy to learn R programming and data science. If you are new to R, have no fear. On this page, we’ll walk you through each of the steps required to begin using swirl today!
<h4>Step 1: Get R</h4>
In order to run swirl, you must have R 3.1.0 or later installed on your computer. If you are on a Linux operating system, please visit our <a href="https://github.com/swirldev/swirl/wiki/Installing-swirl-on-Linux">Installing swirl on Linux</a> page.
If you need to install R, you can do so <a href="http://cran.rstudio.com/">here</a>.

For help installing R, check out one of the following videos (courtesy of Roger Peng at Johns Hopkins Biostatistics):

<a href="http://youtu.be/mfGFv-iB724">Installing R on Windows</a>
<a href="http://youtu.be/Icawuhf0Yqo">Installing R on Mac</a>

<h4>Step 2 (recommended): Get RStudio</h4>
In addition to R, it’s highly recommended that you install RStudio, which will make your experience with R much more enjoyable.

If you need to install RStudio, you can do so here. Select the appropriate installer for your operating system.
<h4>Step 3: Install swirl</h4>
Open RStudio (or just plain R if you don't have RStudio) and type the following into the console:

<code>> > install.packages("swirl")</code>

Note that the &gt; symbol at the beginning of the line is R's prompt for you type something into the console. We include it here so you know that this command is to be typed into the console and not elsewhere. The part you type begins after &gt;.
<h4>Step 4: Start swirl</h4>
This is the only step that you will repeat every time you want to run swirl. First, you will load the package using the library() function. Then you will call the function that starts the magic! Type the following, pressing Enter after each line:

<code> > library("swirl")</code>
<code> > swirl()</code>

<h4>Step 5: Install an interactive course</h4>
The first time you start swirl, you'll be prompted to install a course. You can either install one of the recommended courses or visit our <a href="https://github.com/swirldev/swirl_courses#swirl-courses">course repository</a> for more options. There are even more courses available from the <a href="http://swirlstats.com/scn/">Swirl Course Network</a>.

If you'd like to install a course that is not part of our course repository, type ?InstallCourses at the R prompt for a list of functions that will help you do so.

<h4>Step 6: Have fun!</h4>
Please visit our Help page if you have trouble completing any of these steps.