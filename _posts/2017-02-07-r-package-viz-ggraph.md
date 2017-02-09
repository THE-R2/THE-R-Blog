---
ID: 1334
post_title: 시각화 패키지 ggraph 소개
author: The-R
post_date: 2017-02-07 20:54:27
post_excerpt: ""
layout: post
permalink: >
  http://the-r.kr/2017/02/07/r-package-viz-ggraph/
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "6"
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
&nbsp;

Layouts

In very short terms, a layout is the vertical and horizontal placement of nodes when plotting a particular graph structure. Conversely, a layout algorithm is an algorithm that takes in a graph structure (and potentially some additional parameters) and return the vertical and horizontal position of the nodes. Often, when people think of network visualizations, they think of node-edge diagrams where strongly connected nodes are attempted to be plotted in close proximity. Layouts can be a lot of other things too though — e.g. hive plots and treemaps. One of the driving factors behind ggraph has been to develop an API where any type of visual representation of graph structures is supported. In order to achieve this we first need a flexible way of defining the layout…

ggraph() and createLayout()

As the layout is a global specification of the spatial position of the nodes it spans all layers in the plot and should thus be defined outside of calls to geoms or stats. In ggraph it is often done as part of the plot initialization using ggraph() — a function equivalent in intent to ggplot(). As a minimum ggraph() must be passed a graph object supported by ggraph:

library(ggraph)
library(igraph)
graph

# Not specifying the layout - defaults to "auto"
ggraph(graph) +
geom_edge_link(aes(colour = factor(year))) +
geom_node_point()
center

Not specifying a layout will make ggraph pick one for you. This is only intended to get quickly up and running. The choice of layout should be deliberate on the part of the user as it will have a great effect on what the end result will communicate. From now on all calls to ggraph() will contain a specification of the layout:

ggraph(graph, layout = 'kk') +
geom_edge_link(aes(colour = factor(year))) +
geom_node_point()
center

If the layout algorithm accepts additional parameters (most do), they can be supplied in the call to ggraph() as well:

ggraph(graph, layout = 'kk', maxiter = 100) +
geom_edge_link(aes(colour = factor(year))) +
geom_node_point()
center

In addition to specifying the layout during plot creation it can also happen separately using createLayout(). This function takes the same arguments as ggraph() but returns a layout_ggraph object that can later be used in place of a graph structure in ggraph call:

layout x y name circular ggraph.index
#&gt; 1 -7.734004 10.085789 1 FALSE 1
#&gt; 2 -8.251559 9.226503 2 FALSE 2
#&gt; 3 -7.205127 10.455535 3 FALSE 3
#&gt; 4 -7.113050 11.326465 4 FALSE 4
#&gt; 5 -7.748919 10.742258 5 FALSE 5
#&gt; 6 -7.355531 9.702643 6 FALSE 6
attributes(layout)
#&gt; $names
#&gt; [1] "x" "y" "name" "circular"
#&gt; [5] "ggraph.index"
#&gt;
#&gt; $row.names
#&gt; [1] 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23
#&gt; [24] 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46
#&gt; [47] 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69
#&gt; [70] 70
#&gt;
#&gt; $class
#&gt; [1] "layout_igraph" "layout_ggraph" "data.frame"
#&gt;
#&gt; $graph
#&gt; IGRAPH DN-- 70 506 --
#&gt; + attr: name (v/c), year (e/n)
#&gt; + edges (vertex names):
#&gt; [1] 1 -&gt;14 1 -&gt;15 1 -&gt;21 1 -&gt;54 1 -&gt;55 2 -&gt;21 2 -&gt;22 3 -&gt;9 3 -&gt;15 4 -&gt;5
#&gt; [11] 4 -&gt;18 4 -&gt;19 4 -&gt;43 5 -&gt;19 5 -&gt;43 6 -&gt;13 6 -&gt;20 6 -&gt;22 7 -&gt;17 8 -&gt;14
#&gt; [21] 8 -&gt;17 9 -&gt;12 9 -&gt;20 9 -&gt;21 9 -&gt;22 9 -&gt;51 11-&gt;19 11-&gt;50 11-&gt;52 11-&gt;53
#&gt; [31] 12-&gt;20 12-&gt;21 12-&gt;22 13-&gt;17 13-&gt;20 13-&gt;21 13-&gt;22 14-&gt;21 14-&gt;22 15-&gt;20
#&gt; [41] 16-&gt;18 16-&gt;41 16-&gt;43 17-&gt;7 17-&gt;8 18-&gt;11 18-&gt;16 18-&gt;19 19-&gt;4 19-&gt;11
#&gt; [51] 19-&gt;16 19-&gt;18 19-&gt;27 20-&gt;6 20-&gt;12 20-&gt;21 20-&gt;22 20-&gt;38 21-&gt;22 21-&gt;51
#&gt; [61] 21-&gt;54 21-&gt;55 22-&gt;20 22-&gt;21 22-&gt;38 22-&gt;51 23-&gt;40 23-&gt;43 23-&gt;50 23-&gt;52
#&gt; [71] 23-&gt;53 23-&gt;60 23-&gt;62 23-&gt;65 23-&gt;68 24-&gt;51 26-&gt;32 26-&gt;35 26-&gt;36 26-&gt;40
#&gt; + ... omitted several edges
#&gt;
#&gt; $circular
#&gt; [1] FALSE
As it is just a data.frame it means that any standard ggplot2 call will work by addressing the nodes. Still, use of the geom_node_*() family provided by ggraph is encouraged as it makes it explicit which part of the data structure is being worked with.

Adding support for new data sources

Out of the box ggraph supports dendrogram and igraph objects natively as well as hclust and network through conversion to one of the above. If there is wish for support for additional classes this can be achieved by adding a set of specific methods to the class. The ggraph source code should be your guide in this but I will briefly describe the methods below:

createLayout.myclass()

This method is responsible for taking a graph structure and returning a layout_ggraph object. The object is just a data.frame with the correct class and attributes added. The class should be c('layout_myclass', 'layout_ggraph', 'data.frame') and it should at least have a graph attribute holding the original graph object as well as a circular attribute with a logical giving whether the layout has been transformed to a circular representation or not. If the graph structure contains any additional information about the nodes this should be added to the data.frame as columns so these are accessible during plotting.

getEdges.layout_myclass()

This method takes the return value of createLayout.myclass() and returns the edges of the graph structure. The return value should be in the form of an edge list with a to and from column giving the indexes of the terminal nodes of the edge. Furthermore, it must contain a circular column, again indicating whether the layout should be considered circular. If there are any additional data attached to the edges in the graph structure these should be added as columns to the data.frame.

getConnection.layout_myclass()

This method is intended to return the shortest path between two nodes as a list of node indexes. This method can be ignored but will result in lack of support for geom_conn_* layers.

layout_myclass_*()

Any type of layout algorithm that needs to be available to this class should be defined as a separate layout_myclass_layoutname() function. This function will be called when 'layoutname' is used in the layout argument in ggraph() or createLayout(). At a minimum each new class should have a layout_myclass_auto() defined.

Layouts abound

There’s a lot of different layouts in ggraph — first and foremost because igraph implements a lot of layouts for drawing node-edge diagrams and all of these are available in ggraph. Additionally, ggraph provides a lot of new layout types and algorithms for your drawing pleasure.

A note on circularity

Some layouts can be shown effectively both in a standard Cartesian projection as well as in a polar projection. The standard approach in ggplot2 has been to change the coordinate system with the addition of e.g. coord_polar(). This approach — while consistent with the grammar — is not optimal for ggraph as it does not allow layers to decide how to respond to circularity. The prime example of this is trying to draw straight lines in a plot using coord_polar(). Instead circularity is part of the layout specification and gets communicated to the layers with the circular column in the data, allowing each layer to respond appropriately. Sometimes standard and circular representations of the same layout get used so often that they get different names. In ggraph they’ll have the same name and only differ in whether or not circular is set to TRUE:

# An arc diagram
ggraph(graph, layout = 'linear') +
geom_edge_arc(aes(colour = factor(year)))
center

# A coord diagram
ggraph(graph, layout = 'linear', circular = TRUE) +
geom_edge_arc(aes(colour = factor(year)))
center

graph # An icicle plot
ggraph(graph, 'partition') +
geom_node_tile(aes(fill = depth), size = 0.25)
center

# A sunburst plot
ggraph(graph, 'partition', circular = TRUE) +
geom_node_arc_bar(aes(fill = depth), size = 0.25)
center

Not every layout has a meaningful circular representation in which cases the circular argument will be ignored.

Node-edge diagram layouts

igraph provides a total of 13 different layout algorithms for classic node-edge diagrams (colloquially referred to as hairballs). Some of these are incredibly simple such as randomly, grid, circle, and star, while others tries to optimize the position of nodes based on different characteristics of the graph. There is no such thing as “the best layout algorithm” as algorithms have been optimized for different scenarios. Experiment with the choices at hand and remember to take the end result with a grain of salt, as it is just one of a range of possible “optimal node position” results. Below is an animation showing the different results of running all applicable igraph layouts on the highschool graph.

library(tweenr)
igraph_layouts 'randomly', 'fr', 'kk', 'drl', 'lgl')
igraph_layouts graph V(graph)$degree layouts layouts_tween statelength = 1, ease = 'cubic-in-out',
nframes = length(igraph_layouts) * 16 + 8)
title_transp for (i in seq_len(length(igraph_layouts) * 16)) {
tmp_layout layout title_alpha p geom_edge_fan(aes(alpha = ..index.., colour = factor(year)), n = 15) +
geom_node_point(aes(size = degree)) +
scale_edge_color_brewer(palette = 'Dark2') +
ggtitle(paste0('Layout: ', layout)) +
theme_void() +
theme(legend.position = 'none',
plot.title = element_text(colour = alpha('black', title_alpha)))
plot(p)
}
unnamed-chunk-12

Hive plots

A hive plot, while still technically a node-edge diagram, is a bit different from the rest as it uses information pertaining to the nodes, rather than the connection information in the graph. This means that hive plots, to a certain extend is more interpretable as well as less vulnerable to small changes in the graph structure. They are less common though, so use will often require some additional explanation.

V(graph)$friends V(graph)$friends = 15, 'many', 'medium'))
ggraph(graph, 'hive', axis = 'friends', sort.by = 'degree') +
geom_edge_hive(aes(colour = factor(year), alpha = ..index..)) +
geom_axis_hive(aes(colour = friends), size = 3, label = FALSE) +
coord_fixed()
center

Hierarchical layouts

Trees and hierarchies are an important subset of graph structures, and ggraph provides a range of layouts optimized for their visual representation. Some of these uses enclosure and position rather than edges to communicate relations (e.g. treemaps and circle packing). Still, these layouts can just as well be used for drawing edges if you wish to:

graph set.seed(1)
ggraph(graph, 'circlepack', weight = 'size') +
geom_node_circle(aes(fill = depth), size = 0.25, n = 50) +
coord_fixed()
center

set.seed(1)
ggraph(graph, 'circlepack', weight = 'size') +
geom_edge_link() +
geom_node_point(aes(colour = depth)) +
coord_fixed()
center

ggraph(graph, 'treemap', weight = 'size') +
geom_node_tile(aes(fill = depth), size = 0.25)
center

ggraph(graph, 'treemap', weight = 'size') +
geom_edge_link() +
geom_node_point(aes(colour = depth))
center

The most recognized tree plot is probably dendrograms though. Both igraph and dendrogram object can be plotted as dendrograms, though only dendrogram objects comes with a build in height information for placing the branch points. For igraph objects this is inferred by the longest ancestral length:

ggraph(graph, 'dendrogram') +
geom_edge_diagonal()
center

dendrogram ggraph(dendrogram, 'dendrogram') +
geom_edge_elbow()
center

Dendrograms are one of the layouts that are amenable for circular transformations, which can be effective in giving more space at the leafs of the tree at the expense of the space given to the root:

ggraph(dendrogram, 'dendrogram', circular = TRUE) +
geom_edge_elbow() +
coord_fixed()
center

More to come

This concludes the first of the introduction posts about ggraph. I hope I have been effective in describing the use of layouts and illustrating how they can have a very profound effect on the resulting plot. Stay tuned for more…
<blockquote>In the first post in a series of ggraph introductions I will talk about how ggraph specifies and uses layouts</blockquote>
소스: <em><a href="http://www.data-imaginist.com/2017/ggraph-introduction-layouts/">Data Imaginist - Introduction to ggraph: Layouts</a></em>