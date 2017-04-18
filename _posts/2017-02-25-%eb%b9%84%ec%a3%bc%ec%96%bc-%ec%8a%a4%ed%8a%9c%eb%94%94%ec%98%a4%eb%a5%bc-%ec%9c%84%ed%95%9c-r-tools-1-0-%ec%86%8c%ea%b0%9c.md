---
ID: 1454
post_title: >
  비주얼 스튜디오를 위한 R Tools
  1.0 소개
author: The-R
post_date: 2017-02-25 12:52:58
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/02/25/%eb%b9%84%ec%a3%bc%ec%96%bc-%ec%8a%a4%ed%8a%9c%eb%94%94%ec%98%a4%eb%a5%bc-%ec%9c%84%ed%95%9c-r-tools-1-0-%ec%86%8c%ea%b0%9c/'
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "36"
swp_cache_timestamp:
  - "413331"
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
scc_share_count_google+:
  - "0"
scc_share_count_facebook:
  - "-1"
scc_share_count_pocket:
  - "0"
scc_share_count_hatebu:
  - "0"
scc_share_count_crawldate:
  - 2017/04/18 08:56:56
scc_share_count_total:
  - "0"
dsq_thread_id:
  - "5707873075"
yst_is_cornerstone:
  - ""
---
After more than a year in preview <a href="http://microsoft.github.io/RTVS-docs/" target="_blank" rel="nofollow">R Tools for Visual Studio</a>, the open-source extension to the Visual Studio IDE for R programming, is nearing its official release. RTVS Release Candidate 1 is <a href="http://microsoft.github.io/RTVS-docs/installation.html" target="_blank" rel="nofollow">now available for download</a>, giving you the opportunity to try out the new features ahead of the official announcement.

&nbsp;

<img class="alignnone size-full" src="http://revolution-computing.typepad.com/.a/6a010534b1db25970b01b7c8d95a55970b-800wi" alt="" />

<blockquote>Preview: R Tools for Visual Studio 1.0

&nbsp;</blockquote>

We'll cover the features in detail with the general availability release of RTVS 1.0, but in summary the new features include:

<ul>
    <li><a href="http://microsoft.github.io/RTVS-docs/remote-execution.html" target="_blank" rel="nofollow">Remote Execution</a>: type R code in your local RTVS instance, but have the computations performed on a remote R server. You can also switch between local and remote workspaces at will.</li>
    <li><a href="https://microsoft.github.io/RTVS-docs/sqlserver.html" target="_blank" rel="nofollow">SQL Server Integration</a>: work with database connections and SQL queries, and create stored procedures with embedded R code.</li>
    <li><a href="https://microsoft.github.io/RTVS-docs/plotting.html" target="_blank" rel="nofollow">Enhanced R Graphics Support</a>: multiple floating and dockable plot windows, each with plot history.</li>
</ul>

RTVS works with all flavours of R on Windows: CRAN R, Microsoft R Open, and Microsoft R Client &amp; Server. It requires Visual Studio 2015 (including the free Community edition). The RTVS team welcomes your feedback: you can report issues or offer suggestions via the <a href="https://github.com/Microsoft/RTVS" target="_blank" rel="nofollow">RTVS Github repository</a>. To get started with RTVS, follow the link below.

R Tools for Visual Studio: <a href="http://microsoft.github.io/RTVS-docs/" target="_blank" rel="nofollow">Welcome to R Tools for Visual Studio Preview!</a>

&nbsp;

소스: <em>Preview: R Tools for Visual Studio 1.0 | R-bloggers</em>