---
ID: 1347
post_title: '지리정보 데이터를 맵핑하는 방법: USA 강들 by SHARP SIGHT LABS'
author: The-R
post_date: 2017-02-08 09:42:54
post_excerpt: ""
layout: post
permalink: >
  http://the-r.kr/2017/02/08/r-package-viz-maptools/
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "5"
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
<h4>R 코드</h4>

지도를 생성하기 위한 R 코드는 다음과 같습니다.

<blockquote>#===============
# LOAD PACKAGES
#===============
library(tidyverse)
library(maptools)

#===============
# GET RIVER DATA
#===============

#==========
# LOAD DATA
#==========

#DEFINE URL
# - this is the location of the file
url.river_data % glimpse()

levels(lines.rivers$FEATURE)
table(lines.rivers$FEATURE)

#==============================================
# REMOVE MISC FEATURES
# - there are some features in the data that we
# want to remove
#==============================================
lines.rivers ,"Shoreline Intermittent"
,"Null"
,"Closure Line"
,"Apparent Limit"
)))

# RE-INSPECT
table(lines.rivers$FEATURE)

#==============
# REMOVE STATES
#==============

#-------------------------------
# IDENTIFY STATES
# - we need to find out
# which states are in the data
#-------------------------------
table(lines.rivers$STATE)

#---------------------------------------------------------
# REMOVE STATES
# - remove Alaska, Hawaii, Puerto Rico, and Virgin Islands
# - these are hard to plot in a confined window, so
# we'll remove them for convenience
#---------------------------------------------------------

lines.rivers

# RE-INSPECT
table(lines.rivers$STATE)

#============================================
# FORTIFY
# - fortify will convert the
# 'SpatialLinesDataFrame' to a proper
# data frame that we can use with ggplot2
#============================================

df.usa_rivers

#============
# GET USA MAP
#============
map.usa_country map.usa_states

#=======
# PLOT
#=======

ggplot() +
geom_polygon(data = map.usa_country, aes(x = long, y = lat, group = group), fill = "#484848") +
geom_path(data = df.usa_rivers, aes(x = long, y = lat, group = group), color = "#8ca7c0", size = .08) +
coord_map(projection = "albers", lat0 = 30, lat1 = 40, xlim = c(-121,-73), ylim = c(25,51)) +
labs(title = "Rivers and waterways of the United States") +
annotate("text", label = "sharpsightlabs.com", family = "Gill Sans", color = "#A1A1A1"
, x = -89, y = 26.5, size = 5) +
theme(panel.background = element_rect(fill = "#292929")
,plot.background = element_rect(fill = "#292929")
,panel.grid = element_blank()
,axis.title = element_blank()
,axis.text = element_blank()
,axis.ticks = element_blank()
,text = element_text(family = "Gill Sans", color = "#A1A1A1")
,plot.title = element_text(size = 34)
)</blockquote>
Use this as practice
If you’ve learned the basics of data visualization in R (namely, ggplot2) and you’re interested in geospatial visualization, use this as a small, narrowly-defined exercize to practice some intermediate skills.

There are at least three things that you can learn and practice with this visualization:

Learn about color: Part of what makes this visualization compelling are the colors. Notice that in the area surrounding the US, we’re not using pure black, but a dark grey. For the title, we’re not using white, but a medium grey. Also, notice that for the rivers, we’re not using “blue” but a very specific hexadecimal color. These are all deliberate choices. As an exercise, I highly recommend modifying the colors. Play around a bit and see how changing the colors changes the “feel” of the visualization.
Learn to build visualizations in layers: I’ve emphasized this several times recently, but layering is an important principle of data visualization. Notice that we’re layering the river data over the USA country map. As an exercise, you could also layer in the state boundaries between the country map and the rivers. To do this, you can use map_data().

Learn about ‘Spatial’ data: R has several classes for dealing with ‘geospatial’ data, such as ‘SpatialLines‘, ‘SpatialPoints‘, and others. Spatial data is a whole different animal, so you’ll have to learn its structure. This example will give you a little experience dealing with it.
Iterate to get the details right
What really makes this visualization work is the fine little details. In particular, the size of the lines and the colors.

The reality is that creating good-looking visualizations requires attention to the little details.

To get the details right for a plot like this, I recommend that you build the visualization iteratively.

Start with a simple version of just the map of the US.
<blockquote>ggplot() +
geom_polygon(data = map.usa_country, aes(x = long, y = lat, group = group), fill = "#484848")</blockquote>
Next, layer on the rivers:
<blockquote>ggplot() +
geom_polygon(data = map.usa_country, aes(x = long, y = lat, group = group), fill = "#484848") +
geom_path(data = df.usa_rivers, aes(x = long, y = lat, group = group))</blockquote>
Make no mistake: this doesn’t look good. But, in the early stages, that’s not the goal. You just want to make sure that the data are structurally right. You want something simple that you can build on.

Ok, next, play with the river colors.

Start with a simple ‘blue‘:
<blockquote>ggplot() +
geom_polygon(data = map.usa_country, aes(x = long, y = lat, group = group), fill = "#484848") +
geom_path(data = df.usa_rivers, aes(x = long, y = lat, group = group), color = "blue")</blockquote>
Let’s be honest. This still does not look good.

But it’s closer.

From here, you can play with the colors some more. Select a new color (I recommend using a color picker), and modify the color = aesthetic for geom_path().
<blockquote>ggplot() +
geom_polygon(data = map.usa_country, aes(x = long, y = lat, group = group), fill = "#484848") +
geom_path(data = df.usa_rivers, aes(x = long, y = lat, group = group), color = "#99ccff")</blockquote>
Not perfect, but better still.

From here, you can continue to iterate, add more details, and get them all “perfect”:

The exact color (this takes lots of trial-and-error, and a bit of good taste)
The line size for geom_path()
The title and text annotations
Modify the projection, and change it to the “albers” projection with coord_map()
The other theme() details like background color, removing extraneous elements (like the axis labels) etc
Once again: getting this just right takes lots of iteration. Try it yourself and build this visualization from the bottom up.

Learn ggplot2 (because ggplot2 makes this easy)
In this post, we’ve used ggplot2 to create this particular visualization. While I would classify this visualization at an “intermediate” level, ggplot2 still makes it relatively easy.

That said, if you’re interested in data science and data visualization, learn ggplot2.

Longtime readers at Sharp Sight will know my thoughts on this, but if you’re a new reader this is important.

ggplot2 is almost without question, the best data visualization tool available. Of course, different people will have different needs, but speaking generally, ggplot2 is flexible, powerful, and it allows you to create beautiful data visualizations with relative ease.

Not interested in visualization per se?

Do you want to focus on machine learning instead?

Fair enough.

If you want to learn machine learning, you still need to be able to analyze and explore your data.

Once again, the best tool for exploring and analyzing your data is ggplot2. This is particularly true when you combine it with dplyr, tidyr, stringr, and other tools from the tidyverse.

소스: <em><a href="http://sharpsightlabs.com/blog/map-geospatial-data-usa-rivers/">How to map geospatial data: USA rivers - SHARP SIGHT LABS</a></em>