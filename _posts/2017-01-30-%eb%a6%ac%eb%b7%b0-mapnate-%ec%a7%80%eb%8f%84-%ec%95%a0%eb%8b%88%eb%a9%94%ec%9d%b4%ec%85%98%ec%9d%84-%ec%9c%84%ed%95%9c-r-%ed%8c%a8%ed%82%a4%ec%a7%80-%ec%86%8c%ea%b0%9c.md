---
ID: 1065
post_title: '[리뷰] mapnate &#8211; 지도 애니메이션을 위한 R 패키지 소개'
author: The-R
post_date: 2017-01-30 23:10:49
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/01/30/%eb%a6%ac%eb%b7%b0-mapnate-%ec%a7%80%eb%8f%84-%ec%95%a0%eb%8b%88%eb%a9%94%ec%9d%b4%ec%85%98%ec%9d%84-%ec%9c%84%ed%95%9c-r-%ed%8c%a8%ed%82%a4%ec%a7%80-%ec%86%8c%ea%b0%9c/'
published: true
inline_featured_image:
  - "0"
slide_template:
  - default
fusion_builder_status:
  - ""
avada_post_views_count:
  - "7"
sbg_selected_sidebar:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_replacement:
  - 'a:1:{i:0;s:12:"Blog Sidebar";}'
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
데이터 시각화와 관련하여 수많은 고급 R 패키지들이 사용되고 있습니다. R에는 대부분은 정적인 시각화를 보여주는데 최근에 개발된 패키지들 중에는 동적인 화면을 만들어주는 패키지들도 속속 발표되고 있습니다. mapmate (map animate) 패키지는 지도 애니메이션을위한 R 패키지입니다. 흥미롭게도 이 패키지는 데이터 시각화 애니메이션 제작에 지도 및 지구본 기반의 데이터 애니메이션 사전 제작에 사용됩니다. 주요 기능은 스틸 이미지 시퀀스를 구성하는 일련의 맵 그래픽을 생성하고 디스크에 저장하는데 사용되며 사용자가 선택한 비디오 편집 및 렌더링 소프트웨어에 사용할 수 있습니다. 무엇보다 3D 지구본에 적합합니다.

이번 리뷰에서는 다음과 같은 예제를 다룹니다. 다음의 정지 프레임 시퀀스 생성 :

<ul>
 	<li>평면지도 애니메이션에 사용할지도 데이터</li>
 	<li>정적 지구본 (3D 지구)에 투영되는 동적 / 시간 변화하는 지도 데이터</li>
 	<li>회전하는 지구본에 투영되는 정적 지도 데이터</li>
 	<li>회전하는 지구본에 투영된 동적 지도 데이터</li>
</ul>

Functionality and fine-grain user control of inputs and outputs are limited in the current package version. Other features and functionality will be added in future package versions. While this is a very early developmental stage package, it can also be considered sufficiently complete for its purposes. The primary purpose I had for throwing this package together was to provide a relatively small and simple reproducible example of still image sequence generation similar to those I have used in data animations I’ve shared previously (see bottom of post for examples). The common request I receive is of course for R code.

현재 패키지 버전에서는 입력 및 출력의 기능 및 미세 입자 제어가 제한적입니다. 기타 기능은 향후 패키지 버전에 추가 될 예정입니다. 이것은 매우 초기 발달 단계 패키지이지만, 목적을 달성 할만큼 충분히 완성 된 것으로 간주 될 수도 있습니다. 이 패키지를 함께 던지기위한 주된 목적은 이전에 공유했던 데이터 애니메이션에서 사용한 것과 비슷한 스틸 이미지 시퀀스 생성의 상대적으로 작고 간단한 재현 가능한 예제를 제공하는 것이 었습니다. 내가 받는 공통 요청은 물론 R 코드입니다.

While I prefer a world in which all code is shared freely, there are cases where this can be challenging. Some of the R code I write that involves heavy duty data processing is written in the context of particular computing environments, ones which I know almost no one is working in. It’s not the most helpful to share non-reproducible code that no one can use, or code that is written for an environment in which I have access to hundreds of CPUs and terabytes of RAM, if someone wants to duplicate my work on their laptop. That’s why at times I have only been able to provide rough code templates to give people an idea of what I am coding. This package aims to provide some extremely basic but nonetheless explicit, reproducible examples.

모든 코드가 자유롭게 공유되는 세계를 선호하는 반면, 이것이 어려울 수있는 경우가 있습니다. 중대 근무 데이터 처리와 관련하여 작성한 R 코드 중 일부는 특정 컴퓨팅 환경의 맥락에서 작성되었으며 거의 ​​아무도 작업하지 않는다는 것을 알고 있습니다. 아무도 사용할 수없는 재현 불가능한 코드를 공유하는 것이 가장 도움이되지는 않습니다 누군가가 자신의 랩톱에서 작업을 복제하고 싶다면 수백 CPU 및 테라 바이트 RAM에 액세스 할 수있는 환경을 위해 작성된 코드가 필요합니다. 그래서 저는 사람들이 제가 코딩하고있는 것에 대한 아이디어를 줄 수있는 거친 코드 템플릿 만 제공 할 수있었습니다. 이 패키지는 극단적이지만 기본적이지만 그럼에도 명백하고 재현 가능한 예제를 제공하는 것을 목표로합니다.

Ultimately, there is no free lunch. But I have done my best here to put together some code that will work in the usual computing environments, which is not parallelized, and which will not be unacceptably slow to process on the small example datasets provided in the package.

궁극적으로 공짜는 없습니다. 그러나 평행하지 않은 일반적인 컴퓨팅 환경에서 작동 할 수있는 몇 가지 코드를 조합하여 여기에 최선을 다해 패키지에 제공된 작은 예제 데이터 세트에서 처리하기가 너무 느려지지 않을 것입니다.

mapmate has now been updating from version 0.1.0 to 0.2.0 on Github. The key change is the incorporation of new functions, help docs and code examples focused on network maps, which is a more complex map type not previously covered. The new tutorial content below provides a a couple basic code examples for making network maps with mapmate.

mapmate가 Github의 버전 0.1.0에서 0.2.0으로 업데이트되었습니다. 주요 변경 사항은 이전에 다루지 않은보다 복잡한지도 유형 인 네트워크 맵에 초점을 둔 새로운 기능, 도움말 문서 및 코드 예제의 통합입니다. 아래의 새로운 튜토리얼 내용은 맵 메이트와 네트워크 맵을 만들기위한 몇 가지 기본 코드 예제를 제공합니다.

While mapmate is aimed at still image sequence generation, allowing the user to exert full control over how still image sequences are used to produce animations subsequently (GUI video editor, ffmpeg, ImageMagick, etc) and not directly at animating from R, the examples here include the use of the animation package to help you quickly reproduce some basic animated gifs (as long as you have ImageMagick installed on your system). But the takeaway message is that mapmate now has better support for still image map sequence generation when using the network map type based on great circle arc path traversal.

If you are new to mapmate there is also the introductory vignette. The content of this post is available on the mapmate Github pages as well.

mapmate는 스틸 이미지 시퀀스 생성을 목표로하지만, 사용자가 연속적으로 애니메이션을 생성하는 데 사용되는 이미지 시퀀스 (GUI 비디오 편집기, ffmpeg, ImageMagick 등)를 R에서 직접 애니 메이팅하는 방법에 대해 완벽하게 제어 할 수 있도록 허용하는 반면, 여기의 예제 애니메이션 패키지를 사용하여 (시스템에 ImageMagick이 설치되어있는 한) 기본적인 애니메이션 GIF를 신속하게 재현 할 수 있습니다. 그러나 테이크 어웨이 메시지는 대원 호 경로 통과를 기반으로 네트워크 맵 유형을 사용할 때 맵 메이트가 정지 이미지 맵 시퀀스 생성을 더 잘 지원한다는 점입니다. 새로운지도 제작자 인 경우에는 소개 글이 있습니다. 이 게시물의 내용은 mapmate Github 페이지에서도 볼 수 있습니다.

아래와 같이 패키지 설치를 합니다.

1
<code>devtools::install_github("leonawicz/mapmate")</code>

Networks
The save_map function in the mapmate package offers the type="network" map type. This type of map displays networks or pathways defined by overlapping segments traversing along great circle arcs. This map type can be used to display arbitrary line segments as well if such data is provided, but the provided helper functions used here are aimed specifically at drawing great circles.

Setup
Obtain great circle arc endpoints
The first example uses a flat map. Therefore it is important to break lines at the international dateline when preparing the data. In the second example, lines cross the dateline are not split because the segments will be plotted on the globe.

First, begin with the network data set provided in mapmate is a simple data frame of lon/lat locations of various cities and corresponding weights related to population sizes. It must be expanded to a larger, more complex data frame that contains location pairs and, optionally, distances between locations in each pair. gc_endpoints assists with this by simulating some pairs. The resulting data frame contains endpoints of lines that are defined subsequently.

1
2
3
4
5
6
7
8
9
10
library(mapmate)
library(dplyr)

set.seed(192)
data(network)
network

distFun endpoints endpoints
Obtain great circle arcs
Next, we sample based on a combination of weights. This is an arbitrary and optional step. The example is given primarily to make the data set used in these examples smaller in size. More importantly, the gc_arcs helper function is used to further expand the endpoints data frame to one containing sequences of points describing great circle arcs instead of only their endpoints.

The default number of points added between the endpoints of each great circle arc is n=50, but this can be changed and can also differ for each arc (e.g., based on distance between points). As noted, arcs are filled out planning for use with both flat maps and a globes. A group column is used to identify distinct arcs for plotting.

1
2
3
4
5
6
7
8
9
10
11
# take a weighted sample, e.g., favoring larger averaged populations and
# shorter distances
endpoints endpoints Dist_wts)

# expand data frame from endpoints to arcs, each composed of a sequence of
# points
arcs_flat arcs_globe arcs_globe
Obtain great circle arc path sequences
Finally, gc_paths is used to further expand the great circle arcs data frame into one that contains sequences of ordered segments along each arc. The segments can vary in length between distinct arcs and can overlap one another within an arc. The group argument is required to identify distinct arcs in the input data frame. size is required to set an upper limit on the number of points constituting an arc segment; the actual length of the segments is chosen randomly and uniformly between 2 and size. Other arguments are optional.

1
2
3
paths_flat paths_globe paths_globe
Flat map network animation
The direction of arc traversal can also be controlled by the direction argument if desired. This is useful for simulations if the input data are not yet randomized or if the directions simply need to be reversed. First some setup:

1
2
3
4
n png.args clrs ylm Typically, I would leave the default arguments save.plot=TRUE and return.plot=FALSE, but here they are reversed for the purposes of the example. This returns a list of ggplot objects rather than saving png files. Note that I still included the png.args argument even though width and height will be discarded because save_map will take the background color specified by bg intended for png files and use it in the ggplot2 theme applied to the returned plots.

The default background is transparent so I need to include this here since I have changed it to black. I have changed it to black in this example because I am making a reproducible gif for simplicity rather than doing any layering of separate image sequences in a video editor. Below, saveGIF from the animation package is used to make a simple gif from the plot sequence produced by save_map by looping over the list of returned plots.

In summary, this is all a somewhat convoluted scenario to show you a short animated gif representing plots made by save_map. The intended use case for save_map is to simply export the sequence of png files and the user can do whatever they wish with those files subsequently. If literally all you want to do is make a short, simple animated gif of custom plots using a small amount of data, just use the animation package. You do not need mapmate for that. Also, if you are using animation in general, as with the code below, it is dependent on ImageMagick, which you will also have to install.

1
2
3
4
5
6
7
8
9
gglist ylim = ylm, suffix = "2D", png.args = png.args, save.plot = FALSE, return.plot = TRUE)

library(animation)
# you may need to specify a different path on your Windows machine you may
# also need to ensure convert.exe is part of your particular installation
ani.options(convert = "C:/Program Files/ImageMagick-7.0.3-Q16/convert.exe")
saveGIF(for (i in seq_along(gglist)) print(gglist[[i]]), "network2D.gif", interval = 1/20,
ani.width = 600, ani.height = 300)
network2d

This animation-dependent example and the animated gif are not meant to be distractions from the purpose of this package. Despite the example gif, any code here related to animation is beyond the scope of this tutorial. If you have trouble running it, see the animation documentation and just do the following example instead, which is the way mapmate is meant to be used:

1
2
3
4
save_seq(paths_flat, id = "id", n.frames = n, ortho = FALSE, type = "network",
suffix = "2D", png.args = png.args)
# Next, do whatever you want with the files, such as import them to a video
# editing program
Globe network animation
Here is an example plotting network paths along great circle arcs on the globe. Remember that we use the other data set, which was generated with the default breakAtDateline=FALSE in gc_arcs. As a side note, if you redo the above example for flat maps using the unbroken data, paths_globe, you will see why the arc segments are handled differently when preparing data for flat maps vs. for globes.

1
2
3
n png.args clrs 1
2
3
4
5
6
7
8
gglist pt.size = c(1, 1, 3, 2), suffix = "3D", png.args = png.args, save.plot = FALSE,
return.plot = TRUE)

library(animation)
ani.options(convert = "C:/Program Files/ImageMagick-7.0.3-Q16/convert.exe")
saveGIF(for (i in seq_along(gglist)) print(gglist[[i]]), "network3D.gif", interval = 1/20,
ani.width = 600, ani.height = 600)
network3d

Again, normal usage is to just do the following and then use the saved still image sequence with full user control for whatever you like:

1
2
save_seq(paths_globe, id = "id", n.frames = n, col = clrs, type = "network",
pt.size = c(1, 1, 3, 2), suffix = "3D", png.args = png.args)
Here are a couple more advanced animations based on still image sequences of great circle arc network maps produced using mapmate code: