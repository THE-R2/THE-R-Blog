---
ID: 1141
post_title: R에서 구현해보는 TensorFlow
author: The-R
post_date: 2017-02-02 00:06:11
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/02/02/r%ec%97%90%ec%84%9c-%ea%b5%ac%ed%98%84%ed%95%b4%eb%b3%b4%eb%8a%94-tensorflow/'
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "39"
swp_cache_timestamp:
  - "413411"
scc_share_count_google+:
  - "-1"
scc_share_count_facebook:
  - "-1"
scc_share_count_pocket:
  - "-1"
scc_share_count_hatebu:
  - "-1"
scc_share_count_crawldate:
  - "-1"
scc_share_count_total:
  - "-1"
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
머신러닝과 관련하여 요즘 핫하게 뜨고 있는 딥러닝 분야의 솔루션인 TensorFlow 빼놓고 얘기할 수 없읍니다. 많은 사용자를 갖고 있는 이면에는 기능적인 면이나 여러 개발 도구와도 접목이 잘되기 때문이 아닌가 싶습니다.

최근에 R과 접목하여 좋은 기사가 나와 공유하고자 합니다. 개인 블로그에 R과 관련하여 좋을 글을 올리시는 전희원씨의 컬럼에 나와있는 코딩을 따라 해보면서 <img class="alignnone size-medium wp-image-1142" src="http://the-r.kr/wp-content/uploads/2017/02/tensorflow-lead-300x150-1.jpg" alt="" width="300" height="150" />TensorFlow을 R에서 구현해 보심이 어떠실런지요?

출처: <em><a href="http://freesearch.pe.kr/archives/4546">TensorFlow with R | from __future__ import dream</a></em>