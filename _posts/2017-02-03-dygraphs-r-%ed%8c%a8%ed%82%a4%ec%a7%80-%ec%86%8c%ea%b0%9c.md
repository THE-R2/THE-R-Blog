---
ID: 1206
post_title: dygraphs R 패키지 소개
author: The-R
post_date: 2017-02-03 02:30:05
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/02/03/dygraphs-r-%ed%8c%a8%ed%82%a4%ec%a7%80-%ec%86%8c%ea%b0%9c/'
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "2"
slide_template:
  - default
fusion_builder_status:
  - ""
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
---
dygraphs 패키지는 dygraphs JavaScript 차트 라이브러리에 대한 R 인터페이스입니다. R의 시계열 데이터를 차트화할 수있는 풍부한 기능을 제공합니다.

Automatically plots xts time series objects (or any object convertible to xts).
Highly configurable axis and series display (including optional second Y-axis).
Rich interactive features including zoom/pan and series/point highlighting.
Display upper/lower bars (e.g. prediction intervals) around series.
Various graph overlays including shaded regions, event lines, and point annotations.
Use at the R console just like conventional R plots (via RStudio Viewer).
Seamless embedding within R Markdown documents and Shiny web applications.
<ul>
 	<li>자동으로 xts 시계열 개체 (또는 xts로 변환 가능한 모든 개체)를 그립니다.</li>
 	<li>고도로 구성 가능한 축 및 시리즈 디스플레이 (두 번째 Y 축 옵션 포함).</li>
 	<li>줌 / 팬 및 시리즈 / 포인트 강조 표시 등 풍부한 대화 형 기능.</li>
 	<li>시리즈 주변의 위쪽 / 아래쪽 막대 (예 : 예측 간격)를 표시합니다.</li>
 	<li>음영 처리 된 영역, 이벤트 라인 및 포인트 주석을 포함한 다양한 그래프 오버레이</li>
 	<li>기존의 R 플롯 (RStudio 뷰어 사용)과 마찬가지로 R 콘솔에서 사용합니다.</li>
 	<li>R Markdown 문서 및 Shiny 웹 응용 프로그램 내 매끄러운 임베딩.</li>
</ul>
설치

다음과 같이 CRAN에서 dygraphs 패키지를 설치할 수 있습니다.

&gt; install.packages("dygraphs")

R 콘솔, R Markdown 문서 및 Shiny 응용 프로그램에서 dygraph를 사용할 수 있습니다. 자세한 내용은 사이드 바에서 링크 된 사용 설명서를 참조하세요. 아래 예제의 몇 가지 데모와 예제 갤러리의 데모가 있습니다.

Demos

Here’s a simple dygraph created from a multiple time series object:

&gt; library(dygraphs)
&gt; lungDeaths dygraph(lungDeaths)

출처: <em><a href="https://rstudio.github.io/dygraphs/">dygraphs for R</a></em>