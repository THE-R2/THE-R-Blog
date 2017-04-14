---
ID: 1948
post_title: >
  R ggplot2에 대한 히치하이커의
  가이드
author: The-R
post_date: 2017-04-11 18:15:40
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/04/11/r-ggplot2%ec%97%90-%eb%8c%80%ed%95%9c-%ed%9e%88%ec%b9%98%ed%95%98%ec%9d%b4%ec%bb%a4%ec%9d%98-%ea%b0%80%ec%9d%b4%eb%93%9c/'
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "5"
scc_share_count_google+:
  - "0"
scc_share_count_facebook:
  - "-1"
scc_share_count_pocket:
  - "0"
scc_share_count_hatebu:
  - "0"
scc_share_count_crawldate:
  - 2017/04/14 11:23:11
scc_share_count_total:
  - "0"
dsq_thread_id:
  - "5715542628"
dsq_needs_sync:
  - "1"
slide_template:
  - default
yst_is_cornerstone:
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
fusion_builder_status:
  - ""
---
<h1></h1>
<div id="bg">우선 책은 <a href="https://leanpub.com/hitchhikers_ggplot2">여기</a> 에서 책을 받으실 수 있습니다.</div>
<div></div>
<div>

이것은 완벽 해 보이지만 R 패키지의 변경 사항은 항상 책에 포함 된 예제의 변경을 요구합니다. 이것이 전자 형식이이 작업의 목적에 이상적인 이유입니다. 죽은 나무 책 안에 그것을 갇히는 것은 궁극적으로 시간과 자원 낭비입니다.

나의 첫 번째 서적을 제외하고 이것은 또한 나의 첫 번째 공동 작업입니다. 나는 Jodie Burchell과의 50-50 협력에서 그것을 썼다. Jodie는 놀라운 데이터 과학자입니다. 나는 당신이 재현 가능한 연구 등에서 정말 좋은 자료를 찾을 수있는 그녀의 블로그 Standard Error를 읽기를 강력히 권합니다.

</div>
<div></div>
<div>

이 책은 기술 도서입니다. 이 책의 범위는 바로 그 지점으로 가고 글쓰기 스타일은 자세한 지침이있는 요리법과 유사합니다. R의 기초를 알고 있고 아름다운 그림을 만드는 법을 배우고 싶다고 가정합니다.

각 장에서는 다른 유형의 플롯을 만드는 방법을 설명하고 기본 플롯에서 고도로 맞춤화 된 그래프까지 단계별로 안내합니다. 장의 순서는 난이도에 따른다.

</div>
<div></div>
<div>

모든 장은 다른 장과는 독립적입니다. 전체 책을 읽거나 관심있는 부분으로 갈 수 있으며 첫 번째 장을 읽지 않고 지침을 이해하고 예제를 재현하는 것이 쉽다는 것을 확신합니다.

전체적으로이 책에는 받아 들일 수있는 미적 결과를 얻기 위해 237 페이지 (레터 용지 크기)의 다양한 조리법이 포함되어 있습니다. Leanpub에서 무료로 책을 다운로드 할 수 있습니다 (예, 정말로!).

</div>
<div></div>
This is a book that may look complete but changes in R package are always demanding changes in the examples contained within the book. This is why the electronic format is perfect for the purpose of this work. Trapping it inside a dead tree book is ultimately a waste of time and resources in my on view.

Aside from being my first book, this is also my first collaborative work. I wrote it in a 50-50 collaboration with <a href="http://t-redactyl.io/" target="_blank" rel="nofollow">Jodie Burchell</a>. Jodie is an amazing data scientist. I highly recommend reading her blog <a href="http://t-redactyl.io/" target="_blank" rel="nofollow">Standard Error</a> where you can find really good material on Reproducible Research and more.

This is a technical book. The scope of the book is to go straight to the point and the writing style is similar to a recipe with detailed instructions. It is assumed that you know the basics of R and that you want to learn how to create beautiful plots.

Each chapter will explain how to create a different type of plot, and will take you step-by-step from a basic plot to a highly customised graph. The chapters’ order is by degree of difficulty.

Every chapter is independent from the others. You can read the whole book or go to a section of interest and we are sure that it will be easy to understand the instructions and reproduce our examples without reading the first chapters.

In total this book contains 237 pages (letter paper size) of different recipes to obtain an acceptable aesthetic result. You can download the book for <em>free</em> (yes, really!) from <a href="https://leanpub.com/hitchhikers_ggplot2" target="_blank" rel="nofollow">Leanpub</a>.
<h1>How the book started?</h1>
Almost a year ago I finished writing the eleventh tutorial in a series on using ggplot2 I created with Jodie Burchell.

I asked Jodie to co-authors some blog entries when I found her blog and I realised that my interest in Data Science was reflected on her blog. The book comes after those entries on our blogs.

A few weeks later those tutorials evolved into the shape of an ebook. The reason behind it was that what we started to write had an unexpected success. We even had RTs from important people in the R community such as Hadley Wickham. Finally the book was released by Leanpub.

We also included a pack that contains the Rmd files that we used to generate every chart that is displayed in the book.
<h1>Why Leanpub?</h1>
<a href="https://leanpub.com/" target="_blank" rel="nofollow">Leanpub</a> is a platform where you can easily write your book by using MS Word among other writing software and it even has GitHub and Dropbox integration. We went for R Markdown with LaTeX output, and that means that Leanpub is both easy to use and flexible at the same time.

Even more, Leanpub enables the audience to download your books for free, if you allow it, or you can define a price range with a suggested price indication. The website gives the authors a royalty of 90% minus 50 cents per sale (compared to other platforms this is convenient for the authors). You can also sell your books with additional exercises, lessons in video, etc.

For example, last year I updated all the examples contained in the book just a few days after ggplot2 2.2 was released and my readers had a notification email just after I uploaded the new version. People who pay or does not pay for your books can download the newer versions of if for free.

If that’s not enough Leanpub allows you to create bundles and sell your books as a set or you can charge another price for your book plus additional material such as Rmarkdown notebooks, instructional videos and more.
<h1>What I learned from my first book?</h1>
At the moment I am teaching Data Visualization and from my students I learned that good visualizations come after they learn the visualization concepts. Coding cleary helps but coding goes after the fundamentals.

It would be better to teach visualization fundamentals first and not in parallel while coding, and this applies specially when a part of your audience has never wrote code before.

I got a lot of feedback from my students last term. That was really helpful to improve the book and dive some steps in smaller pieces to facilitate the understading of the Grammar of Graphics.

The interested reader may find some remarkable books that can be read before mine. I highly recommend:
<ul>
 	<li><a href="https://www.amazon.com/Data-Visualisation-Handbook-Driven-Design/dp/1473912148/ref=sr_1_2?ie=UTF8&amp;qid=1480128264&amp;sr=8-2&amp;keywords=data+visualization" target="_blank" rel="nofollow">Data Visualisation: A Handbook for Data Driven Design</a></li>
 	<li><a href="https://www.amazon.com/Storytelling-Data-Visualization-Business-Professionals/dp/1119002257/ref=sr_1_1?ie=UTF8&amp;qid=1480128264&amp;sr=8-1&amp;keywords=data+visualization" target="_blank" rel="nofollow">Storytelling with Data: A Data Visualization Guide for Business Professionals</a></li>
 	<li><a href="https://www.amazon.com/Functional-Art-introduction-information-visualization/dp/0321834739/ref=sr_1_3?ie=UTF8&amp;qid=1480128713&amp;sr=8-3&amp;keywords=alberto+cairo" target="_blank" rel="nofollow">The Functional Art: An introduction to information graphics and visualization</a>.</li>
 	<li><a href="https://www.amazon.com/Grammar-Graphics-Statistics-Computing/dp/0387245448" target="_blank" rel="nofollow">The Grammar of Graphics</a></li>
</ul>
Those are really good books that show the fundamentals of Data Visualisation and provide the key concepts and rules needed to communicate effectively with data.

소스: <em><a href="https://www.r-bloggers.com/the-hitchhikers-guide-to-ggplot2-in-r-3/">The Hitchhiker’s Guide to Ggplot2 in R | R-bloggers</a></em>