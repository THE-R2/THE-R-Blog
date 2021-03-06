---
ID: 1417
post_title: 'R 패키지 소개 ggraph: Nodes'
author: The-R
post_date: 2017-02-11 15:23:19
post_excerpt: ""
layout: post
permalink: >
  http://the-r.kr/2017/02/11/r-package-viz-ggraph-nodes/
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "20"
scc_share_count_google+:
  - "0"
scc_share_count_facebook:
  - "-1"
scc_share_count_pocket:
  - "0"
scc_share_count_hatebu:
  - "0"
scc_share_count_crawldate:
  - 2017/03/12 12:26:57
scc_share_count_total:
  - "0"
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
swp_cache_timestamp:
  - "413126"
sbg_selected_sidebar:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_replacement:
  - 'a:1:{i:0;s:0:"";}'
sbg_selected_sidebar_2:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_2_replacement:
  - 'a:1:{i:0;s:0:"";}'
---
<a href="http://www.data-imaginist.com/2017/ggraph-introduction-nodes/"><img class="alignnone size-full" src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-6-1.png" alt="" /></a>

This is the second post in my series of ggraph introductions. The first post introduced the concept of layouts, which is simply a specification on how nodes should be placed on a plane. This post will dive into how the nodes are drawn, once a layout has been calculated.

Nodes

Nodes in a network are the entities that are connected. Sometimes these are also referred to as vertices, but ggraph has opted for this nomenclature and use it consistently. While the nodes in a graph are the abstract concepts of entities, and the layout is their physical placement, the node geoms is the visual manifestation of the entities. Conceptually one can simply think of it in terms of a scatter plot — the layout provides the x, and y coordinates and these can be used to draw nodes in different ways in the plotting window. Actually, due to the design of ggraph the standard scatterplot-like geoms from ggplot2 can be used directly for plotting nodes:

library(ggraph)
library(igraph)
gr <- graph_from_data_frame(highschool)

ggraph(gr, layout = 'kk') + 
    geom_point(aes(x=x, y=y))
center

<a href="http://www.data-imaginist.com/2017/ggraph-introduction-nodes/"><img class="alignnone size-full" src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-2-1.png" alt="" /></a>

The reason this works is that, as discussed in the previous post, layouts return a data.frame of node positions and metadata and this is used as the default plot data:

head(createLayout(gr, layout = 'kk'))
#>            x          y name circular ggraph.index
#> 1  0.2782438  2.4944195    1    FALSE            1
#> 2  0.1365268  3.1063039    2    FALSE            2
#> 3  0.9329938  3.2168940    3    FALSE            3
#> 4 -2.5457734 -1.5139415    4    FALSE            4
#> 5 -2.8447634 -0.2267242    5    FALSE            5
#> 6 -2.9897376  1.7369304    6    FALSE            6
geom_node_*()

While usage of the default ggplot2 is absolutely allowed, ggraph comes with its own set of node geoms. Many of these are direct translations of ggplot2 own geoms like geom_point() so one could wonder why bother to use them.

The first reason is to provide clear code. It is not apparent anywhere that the standard geoms are addressing the nodes and using geom_node_*() makes it clear that this layer will draw nodes.

The second reason is that it will save typing. Since ggraph are in control of the shape of the input data through the layout calculations, it knows that x and y position is encoded in an x and y column. This means that geom_node_* can default the x and y aesthetics so there’s no need to type them:

ggraph(gr, layout = 'kk') + 
    geom_node_point()
center

<a href="http://www.data-imaginist.com/2017/ggraph-introduction-nodes/"><img class="alignnone size-full" src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-4-1.png" alt="" /></a>

sometimes there is a need for addressing the x and y aesthetics, which is still possible, for instance if a partition layout should be inverted:

gr <- graph_from_data_frame(flare$edges, vertices = flare$vertices)

ggraph(gr, layout = 'partition') + 
    geom_node_tile(aes(y = -y, fill = depth))
center

<a href="http://www.data-imaginist.com/2017/ggraph-introduction-nodes/"><img class="alignnone size-full" src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-5-1.png" alt="" /></a>

of course this could also be accomplished by reversing the y-axis using scale_y_reverse() so this is just to illustrate that the defaults are easily overwritten if needed.

The third reason is for the added functionality. All ggraph geoms gets a filter aesthetic that allows you to quickly filter the input data. The use of this can be illustrated when plotting a tree:

ggraph(gr, layout = 'dendrogram', circular = TRUE) + 
    geom_edge_diagonal() + 
    geom_node_point(aes(filter = leaf)) + 
    coord_fixed()
center

<a href="http://www.data-imaginist.com/2017/ggraph-introduction-nodes/"><img class="alignnone size-full" src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-7-1.png" alt="" /></a>

In the above plot only the terminal nodes are drawn by filtering on the logical leaf column provided by the dendrogram layout.

The different node geoms

The usual suspects are of course provided in the form of geom_node_point() (showcased above), geom_node_text(), and geom_node_label(). These works as expected, taking in the usual aesthetics (plus filter). Only x and y are defaulted so everything else must be provided e.g. label which does not defaults to the name column like is done in igraph. One feature sets geom_node_text() and geom_node_label() from their ggplot2 counterparts: both have a repel argument that, when set to TRUE will use the repel functionality provided by the ggrepel package to avoid overlapping text.

Apart from these three geoms there’s a set of geoms mainly useful for spatial node layouts such as treemaps, partition, and circle packing. geom_node_tile() is the ggraph counterpart to ggplot2s geom_tile() while geom_node_circle() and geom_node_arc_bar() maps to ggforces geom_circle() and geom_arc_bar(). Collective for these is that the spatial dimensions of the geoms (e.g. radius, width, and height) are precalculated by their intended layouts and defaulted be the geoms:

ggraph(gr, layout = 'treemap', weight = 'size') + 
    geom_node_tile(aes(fill = depth))
center


all spatial node geoms will be center-based, meaning that the x and y value of the layout will refer to the center of the layout and not e.g. the bottom-left corner. This makes it easier to add labels to spatial layouts as well as using spatial layouts in a non-spatial way:

l <- ggraph(gr, layout = 'partition', circular = TRUE)
l + geom_node_arc_bar(aes(fill = depth)) + 
    coord_fixed()
center

l + geom_edge_diagonal(aes(width = ..index.., alpha = ..index..), lineend = 'round') + 
    scale_edge_width(range = c(0.2, 1.5)) + 
    geom_node_point(aes(colour = depth)) + 
    coord_fixed()
center

More node geoms are sure to appear in ggraph with time but they will generally be quite easily comprehensible due to their strong assemblance to the standard ggplot2 geoms. After all it is just points on a plane…

More to come

This concludes our tour of the different ways to draw nodes in ggraph. Next up is edges and it is fair to say that this is where it really gets exciting. Stay tuned!


<blockquote>In the second post in this series of ggraph introductions I will dive into how nodes are drawn</blockquote><p>소스: <em><a href="http://www.data-imaginist.com/2017/ggraph-introduction-nodes/">Data Imaginist - Introduction to ggraph: Nodes</a></em></p>