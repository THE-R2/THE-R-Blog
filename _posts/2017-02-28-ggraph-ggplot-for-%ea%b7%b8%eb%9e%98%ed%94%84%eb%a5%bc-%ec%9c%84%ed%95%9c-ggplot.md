---
ID: 1515
post_title: 'ggraph: ggplot for 그래프를 위한 ggplot '
author: The-R
post_date: 2017-02-28 23:59:42
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/02/28/ggraph-ggplot-for-%ea%b7%b8%eb%9e%98%ed%94%84%eb%a5%bc-%ec%9c%84%ed%95%9c-ggplot/'
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "45"
swp_cache_timestamp:
  - "413415"
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
  - 2017/04/18 08:56:54
scc_share_count_total:
  - "0"
yst_is_cornerstone:
  - ""
---
<div>

A g<a href="https://en.wikipedia.org/wiki/Graph_(discrete_mathematics)" target="_blank" rel="nofollow">raph</a>, a collection of <a href="http://www.data-imaginist.com/2017/ggraph-introduction-nodes/" target="_blank" rel="nofollow">nodes</a> connected by <a href="http://www.data-imaginist.com/2017/ggraph-introduction-edges/" target="_blank" rel="nofollow">edges</a>, is just data. Whether it's a social network (where nodes are people, and edges are friend relationships), or a decision tree (where nodes are branch criteria or values, and edges decisions), the nature of the graph is easily represented in a data object. It might be represented as a matrix (where rows and columns are nodes, and elements mark whether an edge between them is present) or as a data frame (where each row is an edge, with columns representing the pair of connected nodes).

The trick comes in how you represent a graph visually; there are many different options each with strengths and weaknesses when it comes to interpretation. A graph with many nodes and edges may become an unintelligible hairball without careful arrangement, and including directionality or other attributes of edges or nodes can reveal insights about the data that wouldn't be apparent otherwise. There are many R packages for creating and displaying graphs (<a href="https://mran.microsoft.com/package/igraph/" target="_blank" rel="nofollow">igraph</a> is a popular one, and this <a href="https://cran.r-project.org/web/views/gR.html" target="_blank" rel="nofollow">CRAN task view</a> lists many others) but that's a problem in its own right: an important part of the data exploration process is trying and comparing different visualization options, and the myriad packages and interfaces makes that process difficult for graph data.

Now, there's the new <a href="https://mran.microsoft.com/package/ggraph/" target="_blank" rel="nofollow">ggraph</a> package,  <a href="http://www.data-imaginist.com/2017/Announcing-ggraph/" target="_blank" rel="nofollow">recently published to CRAN</a> by author Thomas Lin Pederson, which promises to make exploring graph data easier. Unlike other graphing packages, ggraph uses the grammar of graphics paradigm of the ggplot2 package, unifying the data structures and attributes associated with graphics. It also includes a <a href="http://www.data-imaginist.com/2017/ggraph-introduction-layouts/" target="_blank" rel="nofollow">wide range of visual representations of graphs</a> — layouts — and makes it easy to switch between them. The basic "mesh" visualization of nodes and edges provides 11 different options for arranging the nodes:

<a class="asset-img-link" href="http://revolution-computing.typepad.com/.a/6a010534b1db25970b01b7c8dac48f970b-pi" target="_blank" rel="nofollow"><img class="asset asset-image at-xid-6a010534b1db25970b01b7c8dac48f970b image-full img-responsive" title="Ggraph-mesh" src="http://revolution-computing.typepad.com/.a/6a010534b1db25970b01b7c8dac48f970b-800wi" alt="Ggraph-mesh" border="0" data-lazy-loaded="true" /></a>

Other types of visualizations are supported, too: hive plots, dendrograms, treemaps, and circle plots, to name just a few. Note that only static graphs are available, though: unlike igraph and some other packages, you can't rearrange the location of the nodes or otherwise manipulate the graphics with a mouse.

For the R programmer, most of the work is done by the <a href="https://www.rdocumentation.org/packages/ggraph/versions/0.1.1/topics/ggraph" target="_blank" rel="nofollow">ggraph</a> function. It's analagous to the ggplot function, except that you don't provide data for the locations of the nodes; their position is selected by an algorithm. (Similarly, layout choices are automatically made for visualization types other than the mesh.) There are also various themes suited to graphs you can use to style your chart: goodbye gridlines and axes; hello labels, annotations and edge arrows.

The ggraph package is <a href="https://mran.microsoft.com/package/ggraph/" target="_blank" rel="nofollow">available on CRAN now</a>, and works with R version 2.10 and later. For more on the ggraph package, see the announcement blog post linked below.

Data Imaginist: <a href="http://www.data-imaginist.com/2017/Announcing-ggraph/" target="_blank" rel="nofollow">Announcing ggraph: A grammar of graphics for relational data</a>

</div>
<div id="jp-relatedposts" class="jp-relatedposts"></div>
소스: <em>ggraph: ggplot for graphs | R-bloggers</em>