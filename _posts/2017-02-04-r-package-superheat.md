---
ID: 1235
post_title: '시각적 자극에 대한 뇌 반응 모델링 &#8211; superheat 패키지'
author: The-R
post_date: 2017-02-04 13:07:41
post_excerpt: ""
layout: post
permalink: >
  http://the-r.kr/2017/02/04/r-package-superheat/
published: true
inline_featured_image:
  - "0"
slide_template:
  - default
fusion_builder_status:
  - ""
avada_post_views_count:
  - "9"
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
swp_cache_timestamp:
  - "413019"
sbg_selected_sidebar:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_replacement:
  - 'a:1:{i:0;s:12:"Blog Sidebar";}'
sbg_selected_sidebar_2:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_2_replacement:
  - 'a:1:{i:0;s:0:"";}'
---
<div class="container-fluid main-container">
<div id="header" class="fluid-row">
<h3 class="title toc-ignore">fMRI 소개</h3>
</div>
<div id="introduction-to-fmri" class="section level2">

이 사례 연구는 UC Berkeley의 Gallant 신경 과학 연구소 (Gallant lab <a href="http://the-r.kr/2017/02/04/r-package-superheat"> 관련 논문 참조)에서 한 개인에 대해 수행한 기능적 자기 공명 영상 (fMRI) 실험에서 수집 한 데이터를 검사합니다. edu / mlpapers / paper_files / NIPS2008_0963.pdf "> 참조1 </a> 및 <a href="https://projecteuclid.org/download/pdfview_1/euclid.aoas/1310562717"> 참조2 </a>).

fMRI는 신경 활동의 간접적인 척도로 간주 될 수있는 뇌의 산소가 공급 된 혈액 흐름을 측정합니다 (두 과정은 상호 연관성이 높음). fMRI 실험에서 얻은 측정치는 뇌의 큐브와 같은 화소 내에서 수십만개 뉴런의 총 응답과 일치합니다. 두뇌를 3D 화소로 세분화하는 것은 이미지를 2D 픽셀로 세분화하는 것과 유사합니다.

</div>
<div id="data" class="section level2">
<h3>The data</h3>
이 데이터에는 1,750 가지의 이미지 (예 : 아기, 집 또는 그림의 영상)에 대한 반응으로 한 개인의 시각 피질에있는 약 1,300개 화소에 대한 fMRI 측정 값 입니다.

진행 상황을 시각화하기 위해 아래 그림은 fMRI 시스템에서 개별 이미지를 보는 모습입니다.

<div class="figure">

<img src="blob:http://the-r.kr/097c0018-4e01-49c0-ba67-1c2f6a918394" alt="An individual viewing an image while in an fMRI machine" />
<p class="caption">fMRI 기기에서 이미지를 보는 개인</p>

</div>
각각의 이미지는 길이 1282 = 16,3841282 = 16,384의 벡터로 표현 될 수 있지만 가보 (Gabor) 웨이블릿 변환을 통해 길이 10,92110,921로 감소 될 수있는 128 × 128128 × 128 픽셀 그레이 스케일 이미지이다.

원시 데이터는 Computational Neuroscience (CRCNS) 데이터 공유 저장소의 협업 연구에 저장되며 여기에서 찾을 수 있습니다. 데이터에 액세스하려면 데이터로 수행 할 작업을 설명하는 CRCNS 계정을 요청해야하지만 이는 매우 간단합니다.
</div>
<div id="loading-superheat" class="section level2">
<h3>Loading Superheat</h3>
Installing the superheat package from github is easy, assuming you have the <code>devtools</code> package installed in R. Simply type the following command:
<pre class="r"><code class="r"><span class="comment"># install devtools if you don't have it already</span>
<span class="identifier">install.packages</span><span class="paren">(</span><span class="string">"devtools"</span><span class="paren">)</span>
<span class="comment"># install the development version of superheat</span>
<span class="identifier">devtools</span><span class="operator">:</span><span class="operator">:</span><span class="identifier">install_github</span><span class="paren">(</span><span class="string">"rlbarter/superheat"</span><span class="paren">)</span></code></pre>
Assuming that you didn’t run into any unfortunate errors when installing the package, you can load the package into R in the normal way.
<pre class="r"><code><span class="keyword">library</span><span class="paren">(</span><span class="identifier">superheat</span><span class="paren">)</span></code></pre>
</div>
<div id="viewing-the-raw-images" class="section level2">
<h3>Viewing the raw images</h3>
<pre class="r"><code class="r"><span class="comment"># some useful libraries</span>
<span class="keyword">library</span><span class="paren">(</span><span class="identifier">ggplot2</span><span class="paren">)</span>
<span class="keyword">library</span><span class="paren">(</span><span class="identifier">dplyr</span><span class="paren">)</span>
<span class="keyword">library</span><span class="paren">(</span><span class="identifier">gridExtra</span><span class="paren">)</span>
<span class="keyword">library</span><span class="paren">(</span><span class="identifier">knitr</span><span class="paren">)</span>
<span class="keyword">library</span><span class="paren">(</span><span class="identifier">RColorBrewer</span><span class="paren">)</span></code></pre>
It is helpful to have an idea of what kind of images the subject was viewing. The raw images are contained in the <code>Stimuli.mat</code> file, and is separated into a set of 1,750 training images (used to train our models) and 120 validation images (used to evaluate model performance).

The code below loads in the data and extracts the training and validation images
<pre class="r"><code class="r"><span class="comment"># a library for loading matlab files</span>
<span class="keyword">library</span><span class="paren">(</span><span class="identifier">R.matlab</span><span class="paren">)</span>
<span class="comment"># load in the stimuli images</span>
<span class="identifier">stimuli</span> <span class="operator">&lt;-</span> <span class="identifier">readMat</span><span class="paren">(</span><span class="string">"raw_data/Stimuli.mat"</span><span class="paren">)</span>
<span class="comment"># extract training stimuli array</span>
<span class="identifier">train.stimuli</span> <span class="operator">&lt;-</span> <span class="identifier">stimuli</span><span class="paren">[</span><span class="paren">[</span><span class="number">1</span><span class="paren">]</span><span class="paren">]</span>
<span class="comment"># extract validation stimuli array</span>
<span class="identifier">val.stimuli</span> <span class="operator">&lt;-</span> <span class="identifier">stimuli</span><span class="paren">[</span><span class="paren">[</span><span class="number">2</span><span class="paren">]</span><span class="paren">]</span>
<span class="comment"># remove the original stimuli object</span>
<span class="identifier">rm</span><span class="paren">(</span><span class="identifier">stimuli</span><span class="paren">)</span></code></pre>
We display four of the training images below using our superheat package.
<pre class="r"><code class="r"><span class="comment"># view some of the images</span>
<span class="identifier">im1</span> <span class="operator">&lt;-</span> <span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">train.stimuli</span><span class="paren">[</span><span class="number">1</span>, <span class="number">128</span><span class="operator">:</span><span class="number">1</span>, <span class="paren">]</span>, 
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"black"</span>, <span class="string">"white"</span><span class="paren">)</span>,
          <span class="identifier">legend</span> <span class="operator">=</span> <span class="literal">FALSE</span>,
          <span class="identifier">print.plot</span> <span class="operator">=</span> <span class="literal">F</span><span class="paren">)</span>
<span class="identifier">im2</span> <span class="operator">&lt;-</span> <span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">train.stimuli</span><span class="paren">[</span><span class="number">3</span>, <span class="number">128</span><span class="operator">:</span><span class="number">1</span>, <span class="paren">]</span>, 
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"black"</span>, <span class="string">"white"</span><span class="paren">)</span>,
          <span class="identifier">legend</span> <span class="operator">=</span> <span class="literal">FALSE</span>,
          <span class="identifier">print.plot</span> <span class="operator">=</span> <span class="literal">F</span><span class="paren">)</span>
<span class="identifier">im3</span> <span class="operator">&lt;-</span> <span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">train.stimuli</span><span class="paren">[</span><span class="number">10</span>, <span class="number">128</span><span class="operator">:</span><span class="number">1</span>, <span class="paren">]</span>, 
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"black"</span>, <span class="string">"white"</span><span class="paren">)</span>,
          <span class="identifier">legend</span> <span class="operator">=</span> <span class="literal">FALSE</span>,
          <span class="identifier">print.plot</span> <span class="operator">=</span> <span class="literal">F</span><span class="paren">)</span>
<span class="identifier">im4</span> <span class="operator">&lt;-</span> <span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">train.stimuli</span><span class="paren">[</span><span class="number">15</span>, <span class="number">128</span><span class="operator">:</span><span class="number">1</span>, <span class="paren">]</span>, 
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"black"</span>, <span class="string">"white"</span><span class="paren">)</span>,
          <span class="identifier">legend</span> <span class="operator">=</span> <span class="literal">FALSE</span>,
          <span class="identifier">print.plot</span> <span class="operator">=</span> <span class="literal">F</span><span class="paren">)</span>
<span class="comment"># place the images in a 2x2 grid</span>
<span class="identifier">grid.arrange</span><span class="paren">(</span><span class="identifier">im1</span><span class="operator">$</span><span class="identifier">plot</span>, <span class="identifier">im2</span><span class="operator">$</span><span class="identifier">plot</span>, <span class="identifier">im3</span><span class="operator">$</span><span class="identifier">plot</span>, <span class="identifier">im4</span><span class="operator">$</span><span class="identifier">plot</span>, <span class="identifier">ncol</span> <span class="operator">=</span> <span class="number">2</span><span class="paren">)</span></code></pre>
<img src="blob:http://the-r.kr/49ab5a60-4797-411a-8556-4c309037c334" width="576" />

</div>
<div id="preparing-the-data-for-analysis" class="section level2">
<h3>Preparing the data for analysis</h3>
Despite best efforts, sadly not all of the data is publicly available. The Gabor wavelet filters, for example, are not available on the CRCNS website (see above), but the dedicated reader can try to generate their own Gabor wavelets using the raw images contained in Stimuli.mat (see <a href="https://rlbarter.github.io/superheat-examples/fMRI/#data">above</a>).
<div id="gabor-wavelet-features" class="section level3">
<h3>Gabor wavelet features</h3>
I, however, have access to a file, <code>fMRIdata.RData</code> which contains the Gabor wavelet features for the training and validation set images. These Gabor feature matrices are contained in the <code>fit_feat</code> and <code>val_feat</code> objects from the fMRIdata.Rdata file (again, this is unfortunately not publicly available).
<pre class="r"><code class="r"><span class="comment"># load in the gabor wavelet filters</span>
<span class="identifier">load</span><span class="paren">(</span><span class="string">"processed_data/fMRIdata.RData"</span><span class="paren">)</span> <span class="comment"># not available in github</span>
<span class="comment"># fit_feat contains the gabor wavelet features for the 1750 training images</span>
<span class="identifier">train.feat</span> <span class="operator">&lt;-</span> <span class="identifier">fit_feat</span>
<span class="identifier">dim</span><span class="paren">(</span><span class="identifier">train.feat</span><span class="paren">)</span></code></pre>
<pre><code>## [1]  1750 10921</code></pre>
<pre class="r"><code class="r"><span class="comment"># val_feat contains the gabor wavelet features for the 120 validation images</span>
<span class="identifier">val.feat</span> <span class="operator">&lt;-</span> <span class="identifier">val_feat</span>
<span class="identifier">dim</span><span class="paren">(</span><span class="identifier">val.feat</span><span class="paren">)</span></code></pre>
<pre><code>## [1]   120 10921</code></pre>
<pre class="r"><code class="r"><span class="comment"># Remove the other objects that correspond to the responses of a subset of the voxels</span>
<span class="identifier">rm</span><span class="paren">(</span><span class="identifier">fit_feat</span><span class="paren">)</span>
<span class="identifier">rm</span><span class="paren">(</span><span class="identifier">val_feat</span><span class="paren">)</span>
<span class="identifier">rm</span><span class="paren">(</span><span class="identifier">resp_dat</span><span class="paren">)</span>
<span class="identifier">rm</span><span class="paren">(</span><span class="identifier">loc_dat</span><span class="paren">)</span></code></pre>
</div>
<div id="the-voxel-responses" class="section level3">
<h3>The voxel responses</h3>
The voxel responses to each image was collected for two subjects, “S1” and “S2”. We will restrict our analysis to predicting the voxel response in the V1 region for Subject 1 only (see the image below taken from Matthew Schmolesky’s <a href="http://webvision.med.utah.edu/book/part-ix-psychophysics-of-vision/the-primary-visual-cortex/">Webvision</a>).

<img src="blob:http://the-r.kr/0a5c3040-2991-4c9e-8bad-7b7fede8770e" />

Loading in the voxel responses (from the <code>EstimatedResponses.mat</code> file) involves first converting the .mat file to a format readable by R. Specifically I had to convert the data to version 6 MATLAB file in Octave:
<pre class="r"><code class="r"><span class="comment"># In Octave, run:</span>
<span class="operator">&gt;</span><span class="operator">&gt;</span> <span class="identifier">dat</span> <span class="operator">=</span> <span class="identifier">load</span><span class="paren">(</span><span class="string">"EstimatedResponses.mat"</span><span class="paren">)</span>
<span class="operator">&gt;</span><span class="operator">&gt;</span> <span class="identifier">save</span><span class="paren">(</span><span class="string">"-V6"</span>, <span class="string">"EstimatedResponsesV6.mat"</span>, <span class="string">"dat"</span><span class="paren">)</span></code></pre>
Having converted the original MATLAB file to version 6 MATLAB file, we can load it into R using the <code>R.matlab</code> package.
<pre class="r"><code class="r"><span class="comment"># load in the Version 6 matlab file</span>
<span class="identifier">voxel.response</span> <span class="operator">&lt;-</span> <span class="identifier">readMat</span><span class="paren">(</span><span class="string">"processed_data/EstimatedResponsesV6.mat"</span><span class="paren">)</span><span class="operator">$</span><span class="identifier">dat</span>
<span class="identifier">dimnames</span><span class="paren">(</span><span class="identifier">voxel.response</span><span class="paren">)</span><span class="paren">[</span><span class="paren">[</span><span class="number">1</span><span class="paren">]</span><span class="paren">]</span></code></pre>
<pre><code>## [1] "dataTrnS1" "dataTrnS2" "dataValS1" "dataValS2" "roiS1"     "roiS2"    
## [7] "voxIdxS1"  "voxIdxS2"</code></pre>
We can then filter through the objects contained in this file to extract only the responses for the 1331 V1 voxels to the training and validation images.
<pre class="r"><code class="r"><span class="comment"># extract useful objects</span>
<span class="comment"># the columns of train.resp are the 1,750 training images</span>
<span class="comment"># the rows are the 25,915 voxels</span>
<span class="identifier">train.resp</span> <span class="operator">&lt;-</span> <span class="identifier">voxel.response</span><span class="paren">[</span><span class="paren">[</span><span class="number">1</span><span class="paren">]</span><span class="paren">]</span>
<span class="comment"># the columns of val.resp are the 120 training images</span>
<span class="comment"># the rows are the 25,915 voxels</span>
<span class="identifier">val.resp</span> <span class="operator">&lt;-</span> <span class="identifier">voxel.response</span><span class="paren">[</span><span class="paren">[</span><span class="number">3</span><span class="paren">]</span><span class="paren">]</span>
<span class="comment"># extract the V1 voxels</span>
<span class="identifier">V1.vox.index</span> <span class="operator">&lt;-</span> <span class="identifier">which</span><span class="paren">(</span><span class="identifier">voxel.response</span><span class="paren">[</span><span class="paren">[</span><span class="number">5</span><span class="paren">]</span><span class="paren">]</span><span class="paren">[</span>, <span class="number">1</span><span class="paren">]</span> <span class="operator">==</span> <span class="number">1</span><span class="paren">)</span>
<span class="comment"># there are 1331 V1 voxels</span>
<span class="identifier">length</span><span class="paren">(</span><span class="identifier">V1.vox.index</span><span class="paren">)</span></code></pre>
<pre><code>## [1] 1331</code></pre>
<pre class="r"><code class="r"><span class="comment"># filter train.resp and val.resp to the V1 voxels only</span>
<span class="identifier">train.resp</span> <span class="operator">&lt;-</span> <span class="identifier">train.resp</span><span class="paren">[</span><span class="identifier">V1.vox.index</span>, <span class="paren">]</span>
<span class="identifier">val.resp</span> <span class="operator">&lt;-</span> <span class="identifier">val.resp</span><span class="paren">[</span><span class="identifier">V1.vox.index</span>, <span class="paren">]</span>
<span class="comment"># remove the remaining data</span>
<span class="identifier">rm</span><span class="paren">(</span><span class="identifier">voxel.response</span><span class="paren">)</span></code></pre>
</div>
</div>
<div id="cleaning-the-data" class="section level2">
<h3>Cleaning the data</h3>
The final data objects in our workspace are
<pre class="r"><code class="r"><span class="identifier">ls</span><span class="paren">(</span><span class="paren">)</span>
<span class="comment">##  [1] "im1"            "im2"            "im3"            "im4"           </span>
<span class="comment">##  [5] "train.feat"     "train.resp"     "train.stimuli"  "V1.vox.index"  </span>
<span class="comment">##  [9] "val.feat"       "val.resp"       "val.stimuli"    "voxel.response"</span></code></pre>
where
<ul>
    <li><code>train.stimuli</code>: a <span class="math inline"><span id="MathJax-Element-4-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mn&gt;1750&lt;/mn&gt;&lt;mo&gt;&amp;#x00D7;&lt;/mo&gt;&lt;mn&gt;128&lt;/mn&gt;&lt;mo&gt;&amp;#x00D7;&lt;/mo&gt;&lt;mn&gt;128&lt;/mn&gt;&lt;/math&gt;"><span id="MathJax-Span-20" class="math"><span id="MathJax-Span-21" class="mrow"><span id="MathJax-Span-22" class="mn">1750</span><span id="MathJax-Span-23" class="mo">×</span><span id="MathJax-Span-24" class="mn">128</span><span id="MathJax-Span-25" class="mo">×</span><span id="MathJax-Span-26" class="mn">128</span></span></span><span class="MJX_Assistive_MathML">1750×128×128</span></span></span> array corresponding to the 1,750 raw training images each of dimension <span class="math inline"><span id="MathJax-Element-5-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mn&gt;128&lt;/mn&gt;&lt;mo&gt;&amp;#x00D7;&lt;/mo&gt;&lt;mn&gt;128&lt;/mn&gt;&lt;/math&gt;"><span id="MathJax-Span-27" class="math"><span id="MathJax-Span-28" class="mrow"><span id="MathJax-Span-29" class="mn">128</span><span id="MathJax-Span-30" class="mo">×</span><span id="MathJax-Span-31" class="mn">128</span></span></span><span class="MJX_Assistive_MathML">128×128</span></span></span>.</li>
    <li><code>val.stimuli</code>: a <span class="math inline"><span id="MathJax-Element-6-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mn&gt;120&lt;/mn&gt;&lt;mo&gt;&amp;#x00D7;&lt;/mo&gt;&lt;mn&gt;128&lt;/mn&gt;&lt;mo&gt;&amp;#x00D7;&lt;/mo&gt;&lt;mn&gt;128&lt;/mn&gt;&lt;/math&gt;"><span id="MathJax-Span-32" class="math"><span id="MathJax-Span-33" class="mrow"><span id="MathJax-Span-34" class="mn">120</span><span id="MathJax-Span-35" class="mo">×</span><span id="MathJax-Span-36" class="mn">128</span><span id="MathJax-Span-37" class="mo">×</span><span id="MathJax-Span-38" class="mn">128</span></span></span><span class="MJX_Assistive_MathML">120×128×128</span></span></span> array corresponding to the 120 raw validation images each of dimension <span class="math inline"><span id="MathJax-Element-7-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mn&gt;128&lt;/mn&gt;&lt;mo&gt;&amp;#x00D7;&lt;/mo&gt;&lt;mn&gt;128&lt;/mn&gt;&lt;/math&gt;"><span id="MathJax-Span-39" class="math"><span id="MathJax-Span-40" class="mrow"><span id="MathJax-Span-41" class="mn">128</span><span id="MathJax-Span-42" class="mo">×</span><span id="MathJax-Span-43" class="mn">128</span></span></span><span class="MJX_Assistive_MathML">128×128</span></span></span>.</li>
    <li><code>train.feat</code>: a <span class="math inline"><span id="MathJax-Element-8-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mn&gt;1750&lt;/mn&gt;&lt;mo&gt;&amp;#x00D7;&lt;/mo&gt;&lt;mn&gt;10921&lt;/mn&gt;&lt;/math&gt;"><span id="MathJax-Span-44" class="math"><span id="MathJax-Span-45" class="mrow"><span id="MathJax-Span-46" class="mn">1750</span><span id="MathJax-Span-47" class="mo">×</span><span id="MathJax-Span-48" class="mn">10921</span></span></span><span class="MJX_Assistive_MathML">1750×10921</span></span></span> matrix corresponding to the 10,921 Gabor wavelet features for each of the 1,750 training images.</li>
    <li><code>val.feat</code>: a <span class="math inline"><span id="MathJax-Element-9-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mn&gt;120&lt;/mn&gt;&lt;mo&gt;&amp;#x00D7;&lt;/mo&gt;&lt;mn&gt;10921&lt;/mn&gt;&lt;/math&gt;"><span id="MathJax-Span-49" class="math"><span id="MathJax-Span-50" class="mrow"><span id="MathJax-Span-51" class="mn">120</span><span id="MathJax-Span-52" class="mo">×</span><span id="MathJax-Span-53" class="mn">10921</span></span></span><span class="MJX_Assistive_MathML">120×10921</span></span></span> matrix corresponding to the 10,921 Gabor wavelet features for each of the 120 validation images.</li>
    <li><code>train.resp</code>: a <span class="math inline"><span id="MathJax-Element-10-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mn&gt;1331&lt;/mn&gt;&lt;mo&gt;&amp;#x00D7;&lt;/mo&gt;&lt;mn&gt;1750&lt;/mn&gt;&lt;/math&gt;"><span id="MathJax-Span-54" class="math"><span id="MathJax-Span-55" class="mrow"><span id="MathJax-Span-56" class="mn">1331</span><span id="MathJax-Span-57" class="mo">×</span><span id="MathJax-Span-58" class="mn">1750</span></span></span><span class="MJX_Assistive_MathML">1331×1750</span></span></span> matrix containing the responses of the 1,331 voxels in the V1 region to each of the 1,750 training images.</li>
    <li><code>val.resp</code>: a <span class="math inline"><span id="MathJax-Element-11-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mn&gt;1331&lt;/mn&gt;&lt;mo&gt;&amp;#x00D7;&lt;/mo&gt;&lt;mn&gt;120&lt;/mn&gt;&lt;/math&gt;"><span id="MathJax-Span-59" class="math"><span id="MathJax-Span-60" class="mrow"><span id="MathJax-Span-61" class="mn">1331</span><span id="MathJax-Span-62" class="mo">×</span><span id="MathJax-Span-63" class="mn">120</span></span></span><span class="MJX_Assistive_MathML">1331×120</span></span></span> matrix containing the responses of the 1,331 voxels in the V1 region to each of the 120 validation images.</li>
</ul>
<div id="missing-values" class="section level3">
<h4>Missing values</h4>
Note that of the 1,331 voxels in the V1 region, 37 of them have at least 40% missing responses. So we will remove these voxels.
<pre class="r"><code class="r"><span class="comment"># identify the proportion of missing values for each voxel</span>
<span class="identifier">missing.variables</span> <span class="operator">&lt;-</span> <span class="identifier">apply</span><span class="paren">(</span><span class="identifier">train.resp</span>, <span class="number">1</span>, <span class="keyword">function</span><span class="paren">(</span><span class="identifier">x</span><span class="paren">)</span> <span class="identifier">sum</span><span class="paren">(</span><span class="identifier">is.na</span><span class="paren">(</span><span class="identifier">x</span><span class="paren">)</span><span class="paren">)</span> <span class="operator">/</span> <span class="identifier">length</span><span class="paren">(</span><span class="identifier">x</span><span class="paren">)</span><span class="paren">)</span>
<span class="comment"># print the proportion of missingness for the voxels with at </span>
<span class="comment"># least some missingness.</span>
<span class="identifier">length</span><span class="paren">(</span><span class="identifier">missing.variables</span><span class="paren">[</span><span class="identifier">missing.variables</span> <span class="operator">&gt;</span> <span class="number">0</span><span class="paren">]</span><span class="paren">)</span>
<span class="comment">## [1] 37</span></code></pre>
<pre class="r"><code class="r"><span class="comment"># remove these voxels from the training and validation sets</span>
<span class="identifier">train.resp</span> <span class="operator">&lt;-</span> <span class="identifier">t</span><span class="paren">(</span><span class="identifier">train.resp</span><span class="paren">[</span><span class="identifier">which</span><span class="paren">(</span><span class="identifier">missing.variables</span> <span class="operator">==</span> <span class="number">0</span><span class="paren">)</span>, <span class="paren">]</span><span class="paren">)</span>
<span class="identifier">val.resp</span> <span class="operator">&lt;-</span> <span class="identifier">t</span><span class="paren">(</span><span class="identifier">val.resp</span><span class="paren">[</span><span class="identifier">which</span><span class="paren">(</span><span class="identifier">missing.variables</span> <span class="operator">==</span> <span class="number">0</span><span class="paren">)</span>, <span class="paren">]</span><span class="paren">)</span></code></pre>
<pre class="r"><code class="r"><span class="identifier">save</span><span class="paren">(</span><span class="identifier">train.feat</span>, <span class="identifier">train.resp</span>, <span class="identifier">file</span> <span class="operator">=</span> <span class="string">"processed_data/fmri_training_data.RData"</span><span class="paren">)</span>
<span class="identifier">save</span><span class="paren">(</span><span class="identifier">val.feat</span>, <span class="identifier">val.resp</span>, <span class="identifier">file</span> <span class="operator">=</span> <span class="string">"processed_data/fmri_validation_data.RData"</span><span class="paren">)</span></code></pre>
<pre class="r"><code class="r"><span class="comment"># number of voxels remaining after removing missing values</span>
<span class="identifier">ncol</span><span class="paren">(</span><span class="identifier">train.resp</span><span class="paren">)</span>
<span class="comment">## [1] 1294</span></code></pre>
We now thus have 1,294 voxels in the V1 region.

</div>
</div>
<div id="modeling" class="section level2">
<h3>Modeling</h3>
For each of our models, our goal is to predict the response to the viewing of an image for each of the 1,294 voxels (cubic region in the brain).

That is, we have 1,294 separate models (one for each voxel), where the predictors/variables correspond to the 10,921 Gabor features from the training images.
<div id="feature-selection" class="section level3">
<h4>Feature selection</h4>
To make the problem computationally feasible, we decided to filter the 10,921 Gabor features to the 500 that were most correlated with each voxel.

To identify the correlation of each Gabor feature with each voxel response, we ran the following code (also contained in the <code>code/voxel_cor.R</code> file <a href="https://github.com/rlbarter/superheat-examples/tree/master/fMRI/code">that can be found here</a>) on the statistics department computer cluster at UC Berkeley. You could probably run it on your laptop, but I would advise against it unless you are incredibly patient.
<pre class="r"><code class="r"><span class="keyword">library</span><span class="paren">(</span><span class="identifier">parallel</span><span class="paren">)</span>

<span class="identifier">nCores</span> <span class="operator">&lt;-</span> <span class="number">24</span>  <span class="comment"># to set manually </span>
<span class="identifier">cl</span> <span class="operator">&lt;-</span> <span class="identifier">makeCluster</span><span class="paren">(</span><span class="identifier">nCores</span><span class="paren">)</span> 

<span class="comment"># export the necessary variables</span>
<span class="identifier">clusterExport</span><span class="paren">(</span><span class="identifier">cl</span>, <span class="identifier">c</span><span class="paren">(</span><span class="string">"train.feat"</span>, <span class="string">"train.resp"</span>, <span class="string">"glmnet"</span><span class="paren">)</span>, 
              <span class="identifier">envir</span><span class="operator">=</span><span class="identifier">environment</span><span class="paren">(</span><span class="paren">)</span><span class="paren">)</span> 
<span class="comment"># calcualte the correlation of each variable with each voxel</span>
<span class="identifier">cor.vox</span> <span class="operator">&lt;-</span> <span class="identifier">parLapply</span><span class="paren">(</span><span class="identifier">cl</span>, <span class="identifier">data.frame</span><span class="paren">(</span><span class="identifier">train.resp</span><span class="paren">)</span>, <span class="keyword">function</span><span class="paren">(</span><span class="identifier">voxel</span><span class="paren">)</span> <span class="paren">{</span>
  <span class="identifier">apply</span><span class="paren">(</span><span class="identifier">train.feat</span>, <span class="number">2</span>, <span class="keyword">function</span><span class="paren">(</span><span class="identifier">feature</span><span class="paren">)</span> <span class="identifier">cor</span><span class="paren">(</span><span class="identifier">voxel</span>, <span class="identifier">feature</span><span class="paren">)</span><span class="paren">)</span>
<span class="paren">}</span><span class="paren">)</span>
<span class="comment"># save the results</span>
<span class="identifier">save</span><span class="paren">(</span><span class="identifier">cor.vox</span>, <span class="identifier">file</span> <span class="operator">=</span> <span class="string">"results/voxel_cor.RData"</span><span class="paren">)</span></code></pre>
Next, to identify the 500 Gabor features that are most correlated with each voxel, we can simply load the correlation data saved above and run the following code.
<pre class="r"><code class="r"><span class="identifier">load</span><span class="paren">(</span><span class="string">"results/voxel_cor.RData"</span><span class="paren">)</span>
<span class="comment"># identify the 500 most correlated features for each variable</span>
<span class="identifier">top.features</span> <span class="operator">&lt;-</span> <span class="identifier">lapply</span><span class="paren">(</span><span class="identifier">cor.vox</span>, <span class="keyword">function</span><span class="paren">(</span><span class="identifier">cor</span><span class="paren">)</span> <span class="paren">{</span>
  <span class="identifier">order</span><span class="paren">(</span><span class="identifier">cor</span>, <span class="identifier">decreasing</span> <span class="operator">=</span> <span class="literal">TRUE</span><span class="paren">)</span><span class="paren">[</span><span class="number">1</span><span class="operator">:</span><span class="number">500</span><span class="paren">]</span>
<span class="paren">}</span><span class="paren">)</span></code></pre>
</div>
</div>
<div id="lasso-ols-model" class="section level2">
<h3>Lasso + OLS model</h3>
We now fit a <a href="https://en.wikipedia.org/wiki/Lasso_(statistics)">lasso linear model</a> to predict the voxel responses to the image stimuli.

The <span class="math inline"><span id="MathJax-Element-12-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mn&gt;1750&lt;/mn&gt;&lt;mo&gt;&amp;#x00D7;&lt;/mo&gt;&lt;mn&gt;500&lt;/mn&gt;&lt;/math&gt;"><span id="MathJax-Span-64" class="math"><span id="MathJax-Span-65" class="mrow"><span id="MathJax-Span-66" class="mn">1750</span><span id="MathJax-Span-67" class="mo">×</span><span id="MathJax-Span-68" class="mn">500</span></span></span><span class="MJX_Assistive_MathML">1750×500</span></span></span> design matrix (feature matrix) can be represented as follows:
<div class="MathJax_Display"><span id="MathJax-Element-13-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: center; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot; display=&quot;block&quot;&gt;&lt;mi&gt;X&lt;/mi&gt;&lt;mo&gt;=&lt;/mo&gt;&lt;mrow&gt;&lt;mo&gt;[&lt;/mo&gt;&lt;mtable columnalign=&quot;center center center center&quot; rowspacing=&quot;4pt&quot; columnspacing=&quot;1em&quot;&gt;&lt;mtr&gt;&lt;mtd&gt;&lt;msub&gt;&lt;mi&gt;x&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mn&gt;1&lt;/mn&gt;&lt;mo&gt;,&lt;/mo&gt;&lt;mn&gt;1&lt;/mn&gt;&lt;/mrow&gt;&lt;/msub&gt;&lt;/mtd&gt;&lt;mtd&gt;&lt;msub&gt;&lt;mi&gt;x&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mn&gt;1&lt;/mn&gt;&lt;mo&gt;,&lt;/mo&gt;&lt;mn&gt;2&lt;/mn&gt;&lt;/mrow&gt;&lt;/msub&gt;&lt;/mtd&gt;&lt;mtd&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;/mtd&gt;&lt;mtd&gt;&lt;msub&gt;&lt;mi&gt;x&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mn&gt;1&lt;/mn&gt;&lt;mo&gt;,&lt;/mo&gt;&lt;mn&gt;500&lt;/mn&gt;&lt;/mrow&gt;&lt;/msub&gt;&lt;/mtd&gt;&lt;/mtr&gt;&lt;mtr&gt;&lt;mtd&gt;&lt;msub&gt;&lt;mi&gt;x&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mn&gt;2&lt;/mn&gt;&lt;mo&gt;,&lt;/mo&gt;&lt;mn&gt;1&lt;/mn&gt;&lt;/mrow&gt;&lt;/msub&gt;&lt;/mtd&gt;&lt;mtd&gt;&lt;msub&gt;&lt;mi&gt;x&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mn&gt;2&lt;/mn&gt;&lt;mo&gt;,&lt;/mo&gt;&lt;mn&gt;2&lt;/mn&gt;&lt;/mrow&gt;&lt;/msub&gt;&lt;/mtd&gt;&lt;mtd&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;/mtd&gt;&lt;mtd&gt;&lt;msub&gt;&lt;mi&gt;x&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mn&gt;2&lt;/mn&gt;&lt;mo&gt;,&lt;/mo&gt;&lt;mn&gt;500&lt;/mn&gt;&lt;/mrow&gt;&lt;/msub&gt;&lt;/mtd&gt;&lt;/mtr&gt;&lt;mtr&gt;&lt;mtd&gt;&lt;mo&gt;&amp;#x22EE;&lt;/mo&gt;&lt;/mtd&gt;&lt;mtd&gt;&lt;mo&gt;&amp;#x22EE;&lt;/mo&gt;&lt;/mtd&gt;&lt;mtd&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;/mtd&gt;&lt;mtd&gt;&lt;mo&gt;&amp;#x22EE;&lt;/mo&gt;&lt;/mtd&gt;&lt;/mtr&gt;&lt;mtr&gt;&lt;mtd&gt;&lt;msub&gt;&lt;mi&gt;x&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mn&gt;1750&lt;/mn&gt;&lt;mo&gt;,&lt;/mo&gt;&lt;mn&gt;1&lt;/mn&gt;&lt;/mrow&gt;&lt;/msub&gt;&lt;/mtd&gt;&lt;mtd&gt;&lt;msub&gt;&lt;mi&gt;x&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mn&gt;1750&lt;/mn&gt;&lt;mo&gt;,&lt;/mo&gt;&lt;mn&gt;2&lt;/mn&gt;&lt;/mrow&gt;&lt;/msub&gt;&lt;/mtd&gt;&lt;mtd&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;/mtd&gt;&lt;mtd&gt;&lt;msub&gt;&lt;mi&gt;x&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mn&gt;1750&lt;/mn&gt;&lt;mo&gt;,&lt;/mo&gt;&lt;mn&gt;500&lt;/mn&gt;&lt;/mrow&gt;&lt;/msub&gt;&lt;/mtd&gt;&lt;/mtr&gt;&lt;/mtable&gt;&lt;mo&gt;]&lt;/mo&gt;&lt;/mrow&gt;&lt;/math&gt;"><span id="MathJax-Span-69" class="math"><span id="MathJax-Span-70" class="mrow"><span id="MathJax-Span-71" class="mi">X</span><span id="MathJax-Span-72" class="mo">=</span><span id="MathJax-Span-73" class="mrow"><span id="MathJax-Span-74" class="mo">⎡⎣⎢⎢⎢⎢</span><span id="MathJax-Span-75" class="mtable"><span id="MathJax-Span-76" class="mtd"><span id="MathJax-Span-77" class="mrow"><span id="MathJax-Span-78" class="msubsup"><span id="MathJax-Span-79" class="mi">x</span><span id="MathJax-Span-80" class="texatom"><span id="MathJax-Span-81" class="mrow"><span id="MathJax-Span-82" class="mn">1</span><span id="MathJax-Span-83" class="mo">,</span><span id="MathJax-Span-84" class="mn">1</span></span></span></span></span></span><span id="MathJax-Span-108" class="mtd"><span id="MathJax-Span-109" class="mrow"><span id="MathJax-Span-110" class="msubsup"><span id="MathJax-Span-111" class="mi">x</span><span id="MathJax-Span-112" class="texatom"><span id="MathJax-Span-113" class="mrow"><span id="MathJax-Span-114" class="mn">2</span><span id="MathJax-Span-115" class="mo">,</span><span id="MathJax-Span-116" class="mn">1</span></span></span></span></span></span><span id="MathJax-Span-140" class="mtd"><span id="MathJax-Span-141" class="mrow"><span id="MathJax-Span-142" class="mo">⋮</span></span></span><span id="MathJax-Span-154" class="mtd"><span id="MathJax-Span-155" class="mrow"><span id="MathJax-Span-156" class="msubsup"><span id="MathJax-Span-157" class="mi">x</span><span id="MathJax-Span-158" class="texatom"><span id="MathJax-Span-159" class="mrow"><span id="MathJax-Span-160" class="mn">1750</span><span id="MathJax-Span-161" class="mo">,</span><span id="MathJax-Span-162" class="mn">1</span></span></span></span></span></span><span id="MathJax-Span-85" class="mtd"><span id="MathJax-Span-86" class="mrow"><span id="MathJax-Span-87" class="msubsup"><span id="MathJax-Span-88" class="mi">x</span><span id="MathJax-Span-89" class="texatom"><span id="MathJax-Span-90" class="mrow"><span id="MathJax-Span-91" class="mn">1</span><span id="MathJax-Span-92" class="mo">,</span><span id="MathJax-Span-93" class="mn">2</span></span></span></span></span></span><span id="MathJax-Span-117" class="mtd"><span id="MathJax-Span-118" class="mrow"><span id="MathJax-Span-119" class="msubsup"><span id="MathJax-Span-120" class="mi">x</span><span id="MathJax-Span-121" class="texatom"><span id="MathJax-Span-122" class="mrow"><span id="MathJax-Span-123" class="mn">2</span><span id="MathJax-Span-124" class="mo">,</span><span id="MathJax-Span-125" class="mn">2</span></span></span></span></span></span><span id="MathJax-Span-143" class="mtd"><span id="MathJax-Span-144" class="mrow"><span id="MathJax-Span-145" class="mo">⋮</span></span></span><span id="MathJax-Span-163" class="mtd"><span id="MathJax-Span-164" class="mrow"><span id="MathJax-Span-165" class="msubsup"><span id="MathJax-Span-166" class="mi">x</span><span id="MathJax-Span-167" class="texatom"><span id="MathJax-Span-168" class="mrow"><span id="MathJax-Span-169" class="mn">1750</span><span id="MathJax-Span-170" class="mo">,</span><span id="MathJax-Span-171" class="mn">2</span></span></span></span></span></span><span id="MathJax-Span-94" class="mtd"><span id="MathJax-Span-95" class="mrow"><span id="MathJax-Span-96" class="mo">.</span><span id="MathJax-Span-97" class="mo">.</span><span id="MathJax-Span-98" class="mo">.</span></span></span><span id="MathJax-Span-126" class="mtd"><span id="MathJax-Span-127" class="mrow"><span id="MathJax-Span-128" class="mo">.</span><span id="MathJax-Span-129" class="mo">.</span><span id="MathJax-Span-130" class="mo">.</span></span></span><span id="MathJax-Span-146" class="mtd"><span id="MathJax-Span-147" class="mrow"><span id="MathJax-Span-148" class="mo">.</span><span id="MathJax-Span-149" class="mo">.</span><span id="MathJax-Span-150" class="mo">.</span></span></span><span id="MathJax-Span-172" class="mtd"><span id="MathJax-Span-173" class="mrow"><span id="MathJax-Span-174" class="mo">.</span><span id="MathJax-Span-175" class="mo">.</span><span id="MathJax-Span-176" class="mo">.</span></span></span><span id="MathJax-Span-99" class="mtd"><span id="MathJax-Span-100" class="mrow"><span id="MathJax-Span-101" class="msubsup"><span id="MathJax-Span-102" class="mi">x</span><span id="MathJax-Span-103" class="texatom"><span id="MathJax-Span-104" class="mrow"><span id="MathJax-Span-105" class="mn">1</span><span id="MathJax-Span-106" class="mo">,</span><span id="MathJax-Span-107" class="mn">500</span></span></span></span></span></span><span id="MathJax-Span-131" class="mtd"><span id="MathJax-Span-132" class="mrow"><span id="MathJax-Span-133" class="msubsup"><span id="MathJax-Span-134" class="mi">x</span><span id="MathJax-Span-135" class="texatom"><span id="MathJax-Span-136" class="mrow"><span id="MathJax-Span-137" class="mn">2</span><span id="MathJax-Span-138" class="mo">,</span><span id="MathJax-Span-139" class="mn">500</span></span></span></span></span></span><span id="MathJax-Span-151" class="mtd"><span id="MathJax-Span-152" class="mrow"><span id="MathJax-Span-153" class="mo">⋮</span></span></span><span id="MathJax-Span-177" class="mtd"><span id="MathJax-Span-178" class="mrow"><span id="MathJax-Span-179" class="msubsup"><span id="MathJax-Span-180" class="mi">x</span><span id="MathJax-Span-181" class="texatom"><span id="MathJax-Span-182" class="mrow"><span id="MathJax-Span-183" class="mn">1750</span><span id="MathJax-Span-184" class="mo">,</span><span id="MathJax-Span-185" class="mn">500</span></span></span></span></span></span></span><span id="MathJax-Span-186" class="mo">⎤⎦⎥⎥⎥⎥</span></span></span></span><span class="MJX_Assistive_MathML MJX_Assistive_MathML_Block">X=[x1,1x1,2...x1,500x2,1x2,2...x2,500⋮⋮...⋮x1750,1x1750,2...x1750,500]</span></span></div>
where <span class="math inline"><span id="MathJax-Element-14-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;msub&gt;&lt;mi&gt;x&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mi&gt;i&lt;/mi&gt;&lt;mo&gt;,&lt;/mo&gt;&lt;mi&gt;j&lt;/mi&gt;&lt;/mrow&gt;&lt;/msub&gt;&lt;/math&gt;"><span id="MathJax-Span-187" class="math"><span id="MathJax-Span-188" class="mrow"><span id="MathJax-Span-189" class="msubsup"><span id="MathJax-Span-190" class="mi">x</span><span id="MathJax-Span-191" class="texatom"><span id="MathJax-Span-192" class="mrow"><span id="MathJax-Span-193" class="mi">i</span><span id="MathJax-Span-194" class="mo">,</span><span id="MathJax-Span-195" class="mi">j</span></span></span></span></span></span><span class="MJX_Assistive_MathML">xi,j</span></span></span> is the <strong><span class="math inline"><span id="MathJax-Element-15-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mi&gt;j&lt;/mi&gt;&lt;/math&gt;"><span id="MathJax-Span-196" class="math"><span id="MathJax-Span-197" class="mrow"><span id="MathJax-Span-198" class="mi">j</span></span></span><span class="MJX_Assistive_MathML">j</span></span></span>th Gabor wavelet feature value for the <span class="math inline"><span id="MathJax-Element-16-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mi&gt;i&lt;/mi&gt;&lt;/math&gt;"><span id="MathJax-Span-199" class="math"><span id="MathJax-Span-200" class="mrow"><span id="MathJax-Span-201" class="mi">i</span></span></span><span class="MJX_Assistive_MathML">i</span></span></span>th image</strong>.

We have 1,294 response vectors (as we fit 1,294 separate models) each of which contains the response for an individual voxel to the <span class="math inline"><span id="MathJax-Element-17-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mn&gt;1750&lt;/mn&gt;&lt;/math&gt;"><span id="MathJax-Span-202" class="math"><span id="MathJax-Span-203" class="mrow"><span id="MathJax-Span-204" class="mn">1750</span></span></span><span class="MJX_Assistive_MathML">1750</span></span></span> training images. The response vector for voxel <span class="math inline"><span id="MathJax-Element-18-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot;&gt;&lt;mi&gt;v&lt;/mi&gt;&lt;mo&gt;&amp;#x2208;&lt;/mo&gt;&lt;mo fence=&quot;false&quot; stretchy=&quot;false&quot;&gt;{&lt;/mo&gt;&lt;mn&gt;1&lt;/mn&gt;&lt;mo&gt;,&lt;/mo&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;mo&gt;.&lt;/mo&gt;&lt;mo&gt;,&lt;/mo&gt;&lt;mn&gt;1294&lt;/mn&gt;&lt;mo fence=&quot;false&quot; stretchy=&quot;false&quot;&gt;}&lt;/mo&gt;&lt;/math&gt;"><span id="MathJax-Span-205" class="math"><span id="MathJax-Span-206" class="mrow"><span id="MathJax-Span-207" class="mi">v</span><span id="MathJax-Span-208" class="mo">∈</span><span id="MathJax-Span-209" class="mo">{</span><span id="MathJax-Span-210" class="mn">1</span><span id="MathJax-Span-211" class="mo">,</span><span id="MathJax-Span-212" class="mo">.</span><span id="MathJax-Span-213" class="mo">.</span><span id="MathJax-Span-214" class="mo">.</span><span id="MathJax-Span-215" class="mo">,</span><span id="MathJax-Span-216" class="mn">1294</span><span id="MathJax-Span-217" class="mo">}</span></span></span><span class="MJX_Assistive_MathML">v∈{1,...,1294}</span></span></span> can be written as:
<div class="MathJax_Display"><span id="MathJax-Element-19-Frame" class="MathJax" style="box-sizing: border-box; display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 14px; text-indent: 0px; text-align: center; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0px; min-height: 0px; border: 0px; padding: 0px; margin: 0px; position: relative;" tabindex="0" data-mathml="&lt;math xmlns=&quot;http://www.w3.org/1998/Math/MathML&quot; display=&quot;block&quot;&gt;&lt;msub&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mtext mathvariant=&quot;bold&quot;&gt;y&lt;/mtext&gt;&lt;/mrow&gt;&lt;mi&gt;v&lt;/mi&gt;&lt;/msub&gt;&lt;mo&gt;=&lt;/mo&gt;&lt;mrow&gt;&lt;mo&gt;[&lt;/mo&gt;&lt;mtable rowspacing=&quot;4pt&quot; columnspacing=&quot;1em&quot;&gt;&lt;mtr&gt;&lt;mtd&gt;&lt;msubsup&gt;&lt;mi&gt;y&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mn&gt;1&lt;/mn&gt;&lt;/mrow&gt;&lt;mi&gt;v&lt;/mi&gt;&lt;/msubsup&gt;&lt;/mtd&gt;&lt;/mtr&gt;&lt;mtr&gt;&lt;mtd&gt;&lt;msubsup&gt;&lt;mi&gt;y&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mn&gt;2&lt;/mn&gt;&lt;/mrow&gt;&lt;mi&gt;v&lt;/mi&gt;&lt;/msubsup&gt;&lt;/mtd&gt;&lt;/mtr&gt;&lt;mtr&gt;&lt;mtd&gt;&lt;mo&gt;&amp;#x22EE;&lt;/mo&gt;&lt;/mtd&gt;&lt;/mtr&gt;&lt;mtr&gt;&lt;mtd&gt;&lt;msubsup&gt;&lt;mi&gt;y&lt;/mi&gt;&lt;mrow class=&quot;MJX-TeXAtom-ORD&quot;&gt;&lt;mn&gt;1750&lt;/mn&gt;&lt;/mrow&gt;&lt;mi&gt;v&lt;/mi&gt;&lt;/msubsup&gt;&lt;/mtd&gt;&lt;/mtr&gt;&lt;/mtable&gt;&lt;mo&gt;]&lt;/mo&gt;&lt;/mrow&gt;&lt;/math&gt;"><span id="MathJax-Span-218" class="math"><span id="MathJax-Span-219" class="mrow"><span id="MathJax-Span-220" class="msubsup"><span id="MathJax-Span-221" class="texatom"><span id="MathJax-Span-222" class="mrow"><span id="MathJax-Span-223" class="mtext">y</span></span></span><span id="MathJax-Span-224" class="mi">v</span></span><span id="MathJax-Span-225" class="mo">=</span><span id="MathJax-Span-226" class="mrow"><span id="MathJax-Span-227" class="mo">⎡⎣⎢⎢⎢⎢⎢</span><span id="MathJax-Span-228" class="mtable"><span id="MathJax-Span-229" class="mtd"><span id="MathJax-Span-230" class="mrow"><span id="MathJax-Span-231" class="msubsup"><span id="MathJax-Span-232" class="mi">y</span><span id="MathJax-Span-233" class="mi">v</span><span id="MathJax-Span-234" class="texatom"><span id="MathJax-Span-235" class="mrow"><span id="MathJax-Span-236" class="mn">1</span></span></span></span></span></span><span id="MathJax-Span-237" class="mtd"><span id="MathJax-Span-238" class="mrow"><span id="MathJax-Span-239" class="msubsup"><span id="MathJax-Span-240" class="mi">y</span><span id="MathJax-Span-241" class="mi">v</span><span id="MathJax-Span-242" class="texatom"><span id="MathJax-Span-243" class="mrow"><span id="MathJax-Span-244" class="mn">2</span></span></span></span></span></span><span id="MathJax-Span-245" class="mtd"><span id="MathJax-Span-246" class="mrow"><span id="MathJax-Span-247" class="mo">⋮</span></span></span><span id="MathJax-Span-248" class="mtd"><span id="MathJax-Span-249" class="mrow"><span id="MathJax-Span-250" class="msubsup"><span id="MathJax-Span-251" class="mi">y</span><span id="MathJax-Span-252" class="mi">v</span><span id="MathJax-Span-253" class="texatom"><span id="MathJax-Span-254" class="mrow"><span id="MathJax-Span-255" class="mn">1750</span></span></span></span></span></span></span><span id="MathJax-Span-256" class="mo">⎤⎦⎥⎥⎥⎥⎥</span></span></span></span><span class="MJX_Assistive_MathML MJX_Assistive_MathML_Block">yv=[y1vy2v⋮y1750v]</span></span></div>
To fit these 1,294 models, the following code was run using the Statistics Department cluster at UC Berkeley. You will not be able to run this code on your laptop.
<pre class="r"><code class="r"><span class="keyword">library</span><span class="paren">(</span><span class="identifier">glmnet</span><span class="paren">)</span>
<span class="keyword">library</span><span class="paren">(</span><span class="identifier">parallel</span><span class="paren">)</span>
<span class="comment"># set up the cluster for parallelization</span>
<span class="identifier">nCores</span> <span class="operator">&lt;-</span> <span class="number">24</span>  <span class="comment"># to set manually </span>
<span class="identifier">cl</span> <span class="operator">&lt;-</span> <span class="identifier">makeCluster</span><span class="paren">(</span><span class="identifier">nCores</span><span class="paren">)</span> 

<span class="comment"># load the CV parameter selection function</span>
<span class="keyword">source</span><span class="paren">(</span><span class="string">"code/select_lambda.R"</span><span class="paren">)</span>

<span class="comment"># fit the lasso model to each voxel using the 1000 most correlated features</span>
<span class="comment"># for the voxel.</span>
<span class="identifier">clusterExport</span><span class="paren">(</span><span class="identifier">cl</span>, <span class="identifier">c</span><span class="paren">(</span><span class="string">"train.feat"</span>, <span class="string">"train.resp"</span>, <span class="string">"glmnet"</span>, <span class="string">"top.features"</span><span class="paren">)</span>, 
              <span class="identifier">envir</span><span class="operator">=</span><span class="identifier">environment</span><span class="paren">(</span><span class="paren">)</span><span class="paren">)</span> 
<span class="identifier">lasso.list</span> <span class="operator">&lt;-</span> <span class="identifier">parLapply</span><span class="paren">(</span><span class="identifier">cl</span>, <span class="number">1</span><span class="operator">:</span><span class="identifier">ncol</span><span class="paren">(</span><span class="identifier">train.resp</span><span class="paren">)</span>, <span class="keyword">function</span><span class="paren">(</span><span class="identifier">voxel</span><span class="paren">)</span> <span class="paren">{</span>
  <span class="identifier">glmnet</span><span class="paren">(</span><span class="identifier">x</span> <span class="operator">=</span> <span class="identifier">train.feat</span><span class="paren">[</span>, <span class="identifier">top.features</span><span class="paren">[</span><span class="paren">[</span><span class="identifier">voxel</span><span class="paren">]</span><span class="paren">]</span><span class="paren">]</span>, 
         <span class="identifier">y</span> <span class="operator">=</span> <span class="identifier">as.vector</span><span class="paren">(</span><span class="identifier">train.resp</span><span class="paren">[</span> , <span class="identifier">voxel</span><span class="paren">]</span><span class="paren">)</span><span class="paren">)</span> 
<span class="paren">}</span><span class="paren">)</span>
<span class="comment"># extract the lambda sequence from each voxel</span>
<span class="comment"># we want to avoid the ends of the sequence</span>
<span class="comment"># note that some sequences terminate early so providing a </span>
<span class="comment"># universal endpoint for the vector sometimes produces an error</span>
<span class="identifier">lambda.seq</span> <span class="operator">&lt;-</span> <span class="identifier">lapply</span><span class="paren">(</span><span class="identifier">lasso.list</span>, <span class="keyword">function</span><span class="paren">(</span><span class="identifier">model</span><span class="paren">)</span> <span class="paren">{</span>
  <span class="identifier">model</span><span class="operator">$</span><span class="identifier">lambda</span><span class="paren">[</span><span class="number">5</span><span class="operator">:</span><span class="identifier">length</span><span class="paren">(</span><span class="identifier">model</span><span class="operator">$</span><span class="identifier">lambda</span><span class="paren">)</span><span class="paren">]</span>
  <span class="paren">}</span><span class="paren">)</span>

<span class="comment"># use CV to select the best lambda for each voxel-model</span>
<span class="comment"># export the necessary variables</span>
<span class="identifier">clusterExport</span><span class="paren">(</span><span class="identifier">cl</span>, <span class="identifier">c</span><span class="paren">(</span><span class="string">"train.feat"</span>, 
                    <span class="string">"train.resp"</span>, <span class="string">"top.features"</span>, 
                    <span class="string">"cv.glmnet"</span>, <span class="string">"lambda.seq"</span><span class="paren">)</span>, 
              <span class="identifier">envir</span><span class="operator">=</span><span class="identifier">environment</span><span class="paren">(</span><span class="paren">)</span><span class="paren">)</span> 
<span class="comment"># the ith entry of selected.lambda corresponds to the </span>
<span class="comment"># best lambda value for voxel i</span>
<span class="identifier">selected.lambda</span> <span class="operator">&lt;-</span> <span class="identifier">selectLambda</span><span class="paren">(</span><span class="identifier">cl</span> <span class="operator">=</span> <span class="identifier">cl</span>, <span class="identifier">x.mat</span> <span class="operator">=</span> <span class="identifier">train.feat</span>, 
                       <span class="identifier">y.mat</span> <span class="operator">=</span> <span class="identifier">train.resp</span>, <span class="identifier">features</span> <span class="operator">=</span> <span class="identifier">top.features</span>, 
                       <span class="identifier">lambda.seq</span> <span class="operator">=</span> <span class="identifier">lambda.seq</span><span class="paren">)</span>
<span class="comment"># save the results</span>
<span class="identifier">save</span><span class="paren">(</span><span class="identifier">lasso.list</span>, <span class="identifier">selected.lambda</span>, <span class="identifier">top.features</span>, 
     <span class="identifier">file</span> <span class="operator">=</span> <span class="string">"results/lasso_results_top500.RData"</span><span class="paren">)</span>
<span class="comment"># stop the cluster</span>
<span class="identifier">stopCluster</span><span class="paren">(</span><span class="identifier">cl</span><span class="paren">)</span></code></pre>
Having run the above code on the cluster and saved the results in the file <code>lasso_results_top500.RData</code>, we can load the results into the current R session and calculate the corresponding voxel response predictions.

First, we can extract the model coefficients for each model (since we saved the results for each possible lambda, we need to filter to the model with the “best” lambda).
<pre class="r"><code class="r"><span class="identifier">load</span><span class="paren">(</span><span class="string">"results/lasso_results_top500.RData"</span><span class="paren">)</span>
<span class="comment"># extract the best model from lasso.list (above) corresponding to the best lambda</span>
<span class="identifier">beta</span> <span class="operator">&lt;-</span> <span class="identifier">lapply</span><span class="paren">(</span><span class="number">1</span><span class="operator">:</span><span class="identifier">length</span><span class="paren">(</span><span class="identifier">lasso.list</span><span class="paren">)</span>, <span class="keyword">function</span><span class="paren">(</span><span class="identifier">voxel</span><span class="paren">)</span> <span class="paren">{</span>
  <span class="identifier">model.index</span> <span class="operator">&lt;-</span> <span class="identifier">which</span><span class="paren">(</span><span class="identifier">lasso.list</span><span class="paren">[</span><span class="paren">[</span><span class="identifier">voxel</span><span class="paren">]</span><span class="paren">]</span><span class="operator">$</span><span class="identifier">lambda</span> <span class="operator">==</span> <span class="identifier">selected.lambda</span><span class="paren">[</span><span class="identifier">voxel</span><span class="paren">]</span><span class="paren">)</span>
  <span class="identifier">as.matrix</span><span class="paren">(</span><span class="identifier">lasso.list</span><span class="paren">[</span><span class="paren">[</span><span class="identifier">voxel</span><span class="paren">]</span><span class="paren">]</span><span class="operator">$</span><span class="identifier">beta</span><span class="paren">)</span><span class="paren">[</span>, <span class="identifier">model.index</span><span class="paren">]</span>
<span class="paren">}</span><span class="paren">)</span></code></pre>
We can also identify which feature was selected (had a non-zero lasso coefficient) by each voxel.
<pre class="r"><code class="r"><span class="comment"># identify the selected features for each voxel</span>
<span class="identifier">selected.features.list</span> <span class="operator">&lt;-</span> <span class="identifier">lapply</span><span class="paren">(</span><span class="number">1</span><span class="operator">:</span><span class="identifier">length</span><span class="paren">(</span><span class="identifier">top.features</span><span class="paren">)</span>, <span class="keyword">function</span><span class="paren">(</span><span class="identifier">voxel</span><span class="paren">)</span> <span class="paren">{</span>
  <span class="comment"># idenitfy which features were selected for the voxel</span>
  <span class="comment"># start with the features used to train the lasso model</span>
  <span class="identifier">voxel.features</span> <span class="operator">&lt;-</span> <span class="identifier">top.features</span><span class="paren">[</span><span class="paren">[</span><span class="identifier">voxel</span><span class="paren">]</span><span class="paren">]</span>
  <span class="comment"># obtain the coefficients for these feautures</span>
  <span class="identifier">voxel.features.selected</span> <span class="operator">&lt;-</span> <span class="identifier">beta</span><span class="paren">[</span><span class="paren">[</span><span class="identifier">voxel</span><span class="paren">]</span><span class="paren">]</span> <span class="operator">!=</span> <span class="number">0</span>
  <span class="comment"># filter the features index and beta vector to the non-zero coefficients</span>
  <span class="identifier">voxel.features</span> <span class="operator">&lt;-</span> <span class="identifier">voxel.features</span><span class="paren">[</span><span class="identifier">voxel.features.selected</span><span class="paren">]</span>
<span class="paren">}</span><span class="paren">)</span></code></pre>
Next, for each voxel we re-fit a classical un-regularized OLS model for each voxel based on the selected (non-zero) coefficients from the corresponding lasso model.
<pre class="r"><code class="r"><span class="comment"># fit an OLS model for each voxel based on the selected features</span>
<span class="identifier">ols.list</span> <span class="operator">&lt;-</span> <span class="identifier">lapply</span><span class="paren">(</span><span class="number">1</span><span class="operator">:</span><span class="identifier">ncol</span><span class="paren">(</span><span class="identifier">train.resp</span><span class="paren">)</span>, <span class="keyword">function</span><span class="paren">(</span><span class="identifier">voxel</span><span class="paren">)</span> <span class="paren">{</span>
  <span class="identifier">voxel.features</span> <span class="operator">&lt;-</span> <span class="identifier">selected.features.list</span><span class="paren">[</span><span class="paren">[</span><span class="identifier">voxel</span><span class="paren">]</span><span class="paren">]</span>
  <span class="comment"># filter the feature matrix to these selected features</span>
  <span class="identifier">voxel.train</span> <span class="operator">&lt;-</span> <span class="identifier">as.data.frame</span><span class="paren">(</span><span class="identifier">train.feat</span><span class="paren">[</span>, <span class="identifier">voxel.features</span><span class="paren">]</span><span class="paren">)</span>
  <span class="identifier">colnames</span><span class="paren">(</span><span class="identifier">voxel.train</span><span class="paren">)</span> <span class="operator">&lt;-</span> <span class="identifier">paste0</span><span class="paren">(</span><span class="string">"X"</span>, <span class="number">1</span><span class="operator">:</span><span class="identifier">ncol</span><span class="paren">(</span><span class="identifier">voxel.train</span><span class="paren">)</span><span class="paren">)</span>
  <span class="identifier">voxel.train</span><span class="operator">$</span><span class="identifier">y</span> <span class="operator">&lt;-</span> <span class="identifier">train.resp</span><span class="paren">[</span>, <span class="identifier">voxel</span><span class="paren">]</span>
  <span class="comment"># fit an OLS model</span>
  <span class="identifier">lm</span><span class="paren">(</span><span class="identifier">y</span> <span class="operator">~</span> ., <span class="identifier">data</span> <span class="operator">=</span> <span class="identifier">voxel.train</span><span class="paren">)</span>
<span class="paren">}</span><span class="paren">)</span></code></pre>
<div id="evaluating-the-model-on-the-validation-set" class="section level3">
<h4>Evaluating the model on the validation set</h4>
The code below extracts the predicted voxel response for the validation set.
<pre class="r"><code class="r"><span class="comment"># calculate the predicted voxel responses for each image in the TRAINING set</span>
<span class="identifier">predictions</span> <span class="operator">&lt;-</span> <span class="identifier">lapply</span><span class="paren">(</span><span class="number">1</span><span class="operator">:</span><span class="identifier">ncol</span><span class="paren">(</span><span class="identifier">val.resp</span><span class="paren">)</span>, <span class="keyword">function</span><span class="paren">(</span><span class="identifier">voxel</span><span class="paren">)</span> <span class="paren">{</span> 
  <span class="comment"># extract the selected Gabor features for the current voxel</span>
  <span class="identifier">voxel.val</span> <span class="operator">&lt;-</span> <span class="identifier">as.data.frame</span><span class="paren">(</span><span class="identifier">val.feat</span><span class="paren">[</span>, <span class="identifier">selected.features.list</span><span class="paren">[</span><span class="paren">[</span><span class="identifier">voxel</span><span class="paren">]</span><span class="paren">]</span><span class="paren">]</span><span class="paren">)</span>
  <span class="identifier">colnames</span><span class="paren">(</span><span class="identifier">voxel.val</span><span class="paren">)</span> <span class="operator">&lt;-</span> <span class="identifier">paste0</span><span class="paren">(</span><span class="string">"X"</span>, <span class="number">1</span><span class="operator">:</span><span class="identifier">ncol</span><span class="paren">(</span><span class="identifier">voxel.val</span><span class="paren">)</span><span class="paren">)</span>
  <span class="comment"># predict the voxel response for the validation images </span>
  <span class="identifier">predict.lm</span><span class="paren">(</span><span class="identifier">ols.list</span><span class="paren">[</span><span class="paren">[</span><span class="identifier">voxel</span><span class="paren">]</span><span class="paren">]</span>, <span class="identifier">voxel.val</span><span class="paren">)</span>
<span class="paren">}</span><span class="paren">)</span></code></pre>
Below we calculate and plot the correlation of the true voxel responses with the predicted voxel responses for each of the 1,294 voxels.
<pre class="r"><code class="r"><span class="comment"># calculate the correlation between the predictions and the true responses for each voxel</span>
<span class="identifier">prediction.cor</span> <span class="operator">&lt;-</span> <span class="identifier">sapply</span><span class="paren">(</span><span class="number">1</span><span class="operator">:</span><span class="identifier">ncol</span><span class="paren">(</span><span class="identifier">val.resp</span><span class="paren">)</span>, <span class="keyword">function</span><span class="paren">(</span><span class="identifier">voxel</span><span class="paren">)</span> <span class="paren">{</span>
  <span class="identifier">cor</span><span class="paren">(</span><span class="identifier">predictions</span><span class="paren">[</span><span class="paren">[</span><span class="identifier">voxel</span><span class="paren">]</span><span class="paren">]</span>, <span class="identifier">val.resp</span><span class="paren">[</span> ,<span class="identifier">voxel</span><span class="paren">]</span><span class="paren">)</span>
<span class="paren">}</span><span class="paren">)</span>
<span class="comment"># convert to data frame</span>
<span class="identifier">prediction.cor</span> <span class="operator">&lt;-</span> <span class="identifier">data.frame</span><span class="paren">(</span><span class="identifier">voxel</span> <span class="operator">=</span> <span class="number">1</span><span class="operator">:</span><span class="identifier">length</span><span class="paren">(</span><span class="identifier">prediction.cor</span><span class="paren">)</span>, <span class="identifier">cor</span> <span class="operator">=</span> <span class="identifier">prediction.cor</span><span class="paren">)</span></code></pre>
<pre class="r"><code class="r"><span class="comment"># plot a histogram of the correlations between the true and predicted voxel responses</span>
<span class="identifier">ggplot</span><span class="paren">(</span><span class="identifier">prediction.cor</span><span class="paren">)</span> <span class="operator">+</span> 
  <span class="identifier">geom_histogram</span><span class="paren">(</span><span class="identifier">aes</span><span class="paren">(</span><span class="identifier">x</span> <span class="operator">=</span> <span class="identifier">cor</span><span class="paren">)</span>, <span class="identifier">col</span> <span class="operator">=</span> <span class="string">"white"</span>, <span class="identifier">binwidth</span> <span class="operator">=</span> <span class="number">0.02</span><span class="paren">)</span> <span class="operator">+</span>
  <span class="identifier">scale_y_continuous</span><span class="paren">(</span><span class="identifier">name</span> <span class="operator">=</span> <span class="string">"Number of voxels"</span><span class="paren">)</span> <span class="operator">+</span>
  <span class="identifier">scale_x_continuous</span><span class="paren">(</span><span class="identifier">name</span> <span class="operator">=</span> <span class="string">"Correlation of predicted and true voxel response"</span><span class="paren">)</span> </code></pre>
<div class="figure">

<img src="blob:http://the-r.kr/286f4aaf-ae96-41e3-99be-e13455199044" alt="A histogram of the correlation of the true voxel response on the validation images and the predicted voxel response on the validation images for each of the 1294 voxels." width="672" />
<p class="caption">A histogram of the correlation of the true voxel response on the validation images and the predicted voxel response on the validation images for each of the 1294 voxels.</p>

</div>
We see that there appear to be two groups of voxels: those whose whose true and predicted correlations are quite low (around 0.2), and another group whose correlations are around 0.6.

</div>
<div id="visualizing-voxel-performance-accross-all-voxels" class="section level3">
<h4>Visualizing voxel performance accross all voxels</h4>
We will now use superheat to simultaneously evaluate the performance of the lasso models for predicting the responses to the validation images of each of the 1294 voxels.

First we will cluster the images and voxels into two groups for visualization purposes.
<pre class="r"><code class="r"><span class="identifier">set.seed</span><span class="paren">(</span><span class="number">384653</span><span class="paren">)</span>
<span class="comment"># calculate row clusters</span>
<span class="identifier">image.clusters</span> <span class="operator">&lt;-</span> <span class="identifier">kmeans</span><span class="paren">(</span><span class="identifier">val.resp</span>, <span class="identifier">centers</span> <span class="operator">=</span> <span class="number">2</span><span class="paren">)</span><span class="operator">$</span><span class="identifier">cluster</span>
<span class="comment"># calcualte column clusters</span>
<span class="identifier">voxel.clusters</span> <span class="operator">&lt;-</span> <span class="identifier">kmeans</span><span class="paren">(</span><span class="identifier">t</span><span class="paren">(</span><span class="identifier">val.resp</span><span class="paren">)</span>, <span class="identifier">centers</span> <span class="operator">=</span> <span class="number">2</span><span class="paren">)</span><span class="operator">$</span><span class="identifier">cluster</span>
<span class="identifier">save</span><span class="paren">(</span><span class="identifier">voxel.clusters</span>, <span class="identifier">file</span> <span class="operator">=</span> <span class="string">"results/voxel_clusters.RData"</span><span class="paren">)</span></code></pre>
Below we plot some examples of images from each cluster clusters. The following presents four images from the first cluster
<pre class="r"><code class="r"><span class="identifier">set.seed</span><span class="paren">(</span><span class="number">23847</span><span class="paren">)</span>
<span class="identifier">four.images.cl1</span> <span class="operator">&lt;-</span> <span class="identifier">sample</span><span class="paren">(</span><span class="identifier">which</span><span class="paren">(</span><span class="identifier">image.clusters</span> <span class="operator">==</span> <span class="number">1</span><span class="paren">)</span>, <span class="number">4</span><span class="paren">)</span>
<span class="identifier">cl1.im1</span> <span class="operator">&lt;-</span> <span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">val.stimuli</span><span class="paren">[</span><span class="identifier">four.images.cl1</span><span class="paren">[</span><span class="number">1</span><span class="paren">]</span>, <span class="number">128</span><span class="operator">:</span><span class="number">1</span>, <span class="paren">]</span>, 
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"black"</span>, <span class="string">"white"</span><span class="paren">)</span>,
          <span class="identifier">legend</span> <span class="operator">=</span> <span class="literal">FALSE</span>,
          <span class="identifier">print.plot</span> <span class="operator">=</span> <span class="literal">FALSE</span><span class="paren">)</span>
<span class="identifier">cl1.im2</span> <span class="operator">&lt;-</span> <span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">val.stimuli</span><span class="paren">[</span><span class="identifier">four.images.cl1</span><span class="paren">[</span><span class="number">2</span><span class="paren">]</span>, <span class="number">128</span><span class="operator">:</span><span class="number">1</span>, <span class="paren">]</span>, 
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"black"</span>, <span class="string">"white"</span><span class="paren">)</span>,
          <span class="identifier">legend</span> <span class="operator">=</span> <span class="literal">FALSE</span>,
          <span class="identifier">print.plot</span> <span class="operator">=</span> <span class="literal">FALSE</span><span class="paren">)</span>
<span class="identifier">cl1.im3</span> <span class="operator">&lt;-</span> <span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">val.stimuli</span><span class="paren">[</span><span class="identifier">four.images.cl1</span><span class="paren">[</span><span class="number">3</span><span class="paren">]</span>, <span class="number">128</span><span class="operator">:</span><span class="number">1</span>, <span class="paren">]</span>, 
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"black"</span>, <span class="string">"white"</span><span class="paren">)</span>,
          <span class="identifier">legend</span> <span class="operator">=</span> <span class="literal">FALSE</span>,
          <span class="identifier">print.plot</span> <span class="operator">=</span> <span class="literal">FALSE</span><span class="paren">)</span>
<span class="identifier">cl1.im4</span> <span class="operator">&lt;-</span> <span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">val.stimuli</span><span class="paren">[</span><span class="identifier">four.images.cl1</span><span class="paren">[</span><span class="number">4</span><span class="paren">]</span>, <span class="number">128</span><span class="operator">:</span><span class="number">1</span>, <span class="paren">]</span>, 
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"black"</span>, <span class="string">"white"</span><span class="paren">)</span>,
          <span class="identifier">legend</span> <span class="operator">=</span> <span class="literal">FALSE</span>,
          <span class="identifier">print.plot</span> <span class="operator">=</span> <span class="literal">FALSE</span><span class="paren">)</span>
<span class="identifier">grid.arrange</span><span class="paren">(</span><span class="identifier">cl1.im1</span><span class="operator">$</span><span class="identifier">plot</span>, <span class="identifier">cl1.im2</span><span class="operator">$</span><span class="identifier">plot</span>, <span class="identifier">cl1.im3</span><span class="operator">$</span><span class="identifier">plot</span>, <span class="identifier">cl1.im4</span><span class="operator">$</span><span class="identifier">plot</span>, <span class="identifier">ncol</span> <span class="operator">=</span> <span class="number">2</span><span class="paren">)</span></code></pre>
<img src="blob:http://the-r.kr/2b3f6b3b-3646-4c9d-8787-7a1615296e37" width="672" />

While the next four images are from the second cluster.
<pre class="r"><code class="r"><span class="identifier">set.seed</span><span class="paren">(</span><span class="number">23847</span><span class="paren">)</span>
<span class="identifier">four.images.cl2</span> <span class="operator">&lt;-</span> <span class="identifier">sample</span><span class="paren">(</span><span class="identifier">which</span><span class="paren">(</span><span class="identifier">image.clusters</span> <span class="operator">==</span> <span class="number">2</span><span class="paren">)</span>, <span class="number">4</span><span class="paren">)</span>
<span class="identifier">cl2.im1</span> <span class="operator">&lt;-</span> <span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">val.stimuli</span><span class="paren">[</span><span class="identifier">four.images.cl2</span><span class="paren">[</span><span class="number">1</span><span class="paren">]</span>, <span class="number">128</span><span class="operator">:</span><span class="number">1</span>, <span class="paren">]</span>, 
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"black"</span>, <span class="string">"white"</span><span class="paren">)</span>,
          <span class="identifier">legend</span> <span class="operator">=</span> <span class="literal">FALSE</span>,
          <span class="identifier">print.plot</span> <span class="operator">=</span> <span class="literal">FALSE</span><span class="paren">)</span>
<span class="identifier">cl2.im2</span> <span class="operator">&lt;-</span> <span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">val.stimuli</span><span class="paren">[</span><span class="identifier">four.images.cl2</span><span class="paren">[</span><span class="number">2</span><span class="paren">]</span>, <span class="number">128</span><span class="operator">:</span><span class="number">1</span>, <span class="paren">]</span>, 
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"black"</span>, <span class="string">"white"</span><span class="paren">)</span>,
          <span class="identifier">legend</span> <span class="operator">=</span> <span class="literal">FALSE</span>,
          <span class="identifier">print.plot</span> <span class="operator">=</span> <span class="literal">FALSE</span><span class="paren">)</span>
<span class="identifier">cl2.im3</span> <span class="operator">&lt;-</span> <span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">val.stimuli</span><span class="paren">[</span><span class="identifier">four.images.cl2</span><span class="paren">[</span><span class="number">3</span><span class="paren">]</span>, <span class="number">128</span><span class="operator">:</span><span class="number">1</span>, <span class="paren">]</span>, 
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"black"</span>, <span class="string">"white"</span><span class="paren">)</span>,
          <span class="identifier">legend</span> <span class="operator">=</span> <span class="literal">FALSE</span>,
          <span class="identifier">print.plot</span> <span class="operator">=</span> <span class="literal">FALSE</span><span class="paren">)</span>
<span class="identifier">cl2.im4</span> <span class="operator">&lt;-</span> <span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">val.stimuli</span><span class="paren">[</span><span class="identifier">four.images.cl2</span><span class="paren">[</span><span class="number">4</span><span class="paren">]</span>, <span class="number">128</span><span class="operator">:</span><span class="number">1</span>, <span class="paren">]</span>, 
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"black"</span>, <span class="string">"white"</span><span class="paren">)</span>,
          <span class="identifier">legend</span> <span class="operator">=</span> <span class="literal">FALSE</span>,
          <span class="identifier">print.plot</span> <span class="operator">=</span> <span class="literal">FALSE</span><span class="paren">)</span>
<span class="identifier">grid.arrange</span><span class="paren">(</span><span class="identifier">cl2.im1</span><span class="operator">$</span><span class="identifier">plot</span>, <span class="identifier">cl2.im2</span><span class="operator">$</span><span class="identifier">plot</span>, <span class="identifier">cl2.im3</span><span class="operator">$</span><span class="identifier">plot</span>, <span class="identifier">cl2.im4</span><span class="operator">$</span><span class="identifier">plot</span>, <span class="identifier">ncol</span> <span class="operator">=</span> <span class="number">2</span><span class="paren">)</span></code></pre>
<img src="blob:http://the-r.kr/46a5c12a-a8bb-4d21-a138-6d54971f853c" width="672" />

Next, we plot a heatmap of the <em>validation response</em> matrix, that is, the response of each voxel to each validation image. Above each column in the heatmap (each column corresponds to a voxel), we plot the correlation of the observed voxel response with the predicted voxel response.
<pre class="r"><code class="r"><span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">val.resp</span>, 
          <span class="identifier">yt</span> <span class="operator">=</span> <span class="identifier">prediction.cor</span><span class="operator">$</span><span class="identifier">cor</span>,
          <span class="identifier">yt.axis.name</span> <span class="operator">=</span> <span class="string">"Correlation between\npredicted and true\nvoxel responses"</span>,
          
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">brewer.pal</span><span class="paren">(</span><span class="number">5</span>, <span class="string">"RdBu"</span><span class="paren">)</span>,
          
          <span class="identifier">yt.obs.col</span> <span class="operator">=</span> <span class="identifier">rep</span><span class="paren">(</span><span class="string">"slategray4"</span>, <span class="identifier">ncol</span><span class="paren">(</span><span class="identifier">val.resp</span><span class="paren">)</span><span class="paren">)</span>,
          <span class="identifier">yt.point.alpha</span> <span class="operator">=</span> <span class="number">0.6</span>,
          <span class="identifier">yt.axis.name.size</span> <span class="operator">=</span> <span class="number">12</span>,
          <span class="identifier">yt.plot.size</span> <span class="operator">=</span> <span class="number">0.7</span>,
          <span class="identifier">yt.point.size</span> <span class="operator">=</span> <span class="number">2</span>,
          
          <span class="identifier">membership.rows</span> <span class="operator">=</span> <span class="identifier">image.clusters</span>,
          <span class="identifier">membership.cols</span> <span class="operator">=</span> <span class="identifier">voxel.clusters</span>,
          
          <span class="identifier">left.label</span> <span class="operator">=</span> <span class="string">"none"</span>,
          <span class="identifier">bottom.label</span> <span class="operator">=</span> <span class="string">"none"</span>,
          <span class="identifier">grid.hline.col</span> <span class="operator">=</span> <span class="string">"white"</span>,
          <span class="identifier">grid.vline.col</span> <span class="operator">=</span> <span class="string">"white"</span>,
          <span class="identifier">grid.hline.size</span> <span class="operator">=</span> <span class="number">2</span>,
          <span class="identifier">grid.vline.size</span> <span class="operator">=</span> <span class="number">2</span>,
          
          <span class="identifier">row.title</span> <span class="operator">=</span> <span class="string">"Validation images (120)"</span>,
          <span class="identifier">column.title</span> <span class="operator">=</span> <span class="string">"Voxels (1,294)"</span>,
          <span class="identifier">title</span> <span class="operator">=</span> <span class="string">"(a)"</span><span class="paren">)</span></code></pre>
<img src="blob:http://the-r.kr/3f024ad4-4477-4b3d-b359-c294ba8cbddc" width="576" />

The heatmap above is very noisy as a lot of information is being crammed into a small number of pixels. It is thus often much easier to “smooth” the heatmap within its clusters to highlight the “big picture”.
<pre class="r"><code class="r"><span class="identifier">superheat</span><span class="paren">(</span><span class="identifier">val.resp</span>, 
          
           <span class="identifier">X.text</span> <span class="operator">=</span> <span class="identifier">matrix</span><span class="paren">(</span><span class="identifier">c</span><span class="paren">(</span><span class="string">"lower\nvoxel\nresponse"</span>,
                            <span class="string">"higher\nvoxel\nresponse"</span>,
                            <span class="string">"neutral\nvoxel\nresponse"</span>, 
                            <span class="string">"neutral\nvoxel\nresponse"</span><span class="paren">)</span>, <span class="identifier">ncol</span> <span class="operator">=</span> <span class="number">2</span><span class="paren">)</span>,
          <span class="identifier">X.text.col</span> <span class="operator">=</span> <span class="identifier">matrix</span><span class="paren">(</span><span class="identifier">c</span><span class="paren">(</span><span class="string">"white"</span>, <span class="string">"white"</span>, <span class="string">"black"</span>, <span class="string">"black"</span><span class="paren">)</span>, <span class="identifier">ncol</span> <span class="operator">=</span> <span class="number">2</span><span class="paren">)</span>,
          
          <span class="identifier">smooth.heat</span> <span class="operator">=</span> <span class="literal">T</span>,
          
          <span class="identifier">heat.pal</span> <span class="operator">=</span> <span class="identifier">brewer.pal</span><span class="paren">(</span><span class="number">5</span>, <span class="string">"RdBu"</span><span class="paren">)</span>,
          
          <span class="identifier">yt</span> <span class="operator">=</span> <span class="identifier">prediction.cor</span><span class="operator">$</span><span class="identifier">cor</span>,
          <span class="identifier">yt.axis.name</span> <span class="operator">=</span> <span class="string">"Correlation between\npredicted and true\nvoxel responses"</span>,
          <span class="identifier">yt.plot.type</span> <span class="operator">=</span> <span class="string">"boxplot"</span>,
          <span class="identifier">yt.cluster.col</span> <span class="operator">=</span> <span class="string">"slategray4"</span>,
          <span class="identifier">yt.axis.name.size</span> <span class="operator">=</span> <span class="number">12</span>,
          <span class="identifier">yt.plot.size</span> <span class="operator">=</span> <span class="number">0.7</span>,
          
          <span class="identifier">membership.rows</span> <span class="operator">=</span> <span class="identifier">image.clusters</span>,
          <span class="identifier">membership.cols</span> <span class="operator">=</span> <span class="identifier">voxel.clusters</span>,
          
          <span class="identifier">left.label</span> <span class="operator">=</span> <span class="string">"none"</span>,
          <span class="identifier">bottom.label</span> <span class="operator">=</span> <span class="string">"none"</span>,
          <span class="identifier">grid.hline.col</span> <span class="operator">=</span> <span class="string">"white"</span>,
          <span class="identifier">grid.vline.col</span> <span class="operator">=</span> <span class="string">"white"</span>,
          <span class="identifier">grid.hline.size</span> <span class="operator">=</span> <span class="number">2</span>,
          <span class="identifier">grid.vline.size</span> <span class="operator">=</span> <span class="number">2</span>,
          
          <span class="identifier">row.title</span> <span class="operator">=</span> <span class="string">"Validation images (120)"</span>,
          <span class="identifier">column.title</span> <span class="operator">=</span> <span class="string">"Voxels (1,294)"</span>,
          <span class="identifier">title</span> <span class="operator">=</span> <span class="string">"(b)"</span><span class="paren">)</span></code></pre>
<pre><code>## [1] -0.30 -0.20 -0.04  0.09  0.20</code></pre>
<img src="blob:http://the-r.kr/59bb0a14-2838-421b-ac1d-3641a13adfb5" width="576" />

What we can see is that the two clusters of voxels behave very differently:
<ul>
    <li>the first cluster of voxels is much more active in response to viewings of images from the second cluster of images than to images from the first cluster.</li>
    <li>the second cluster of voxels does not appear to exhibit a strong difference in response to the two clusters of images.</li>
</ul>
Furthermore, the predicted responses for the first cluster of voxels are much more correlated with the true responses for these voxels, with an average correlation of around 0.5. The predicted responses to the second cluster of voxels, on the other hand, have approximately zero correlation with the true responses exhibited by these voxels.

</div>
</div>
<div id="exploring-the-voxel-clusters" class="section level2">
<h3>Exploring the voxel clusters</h3>
Notice that we found two clusters of voxels that respond to the visual stimuli differently: the first cluster of voxels is highly sensitive to visual stimuli, whereas the second cluster is not.

Our goal is to explore the physical locations of the voxels. We can load in the locations data that can be found on Yuval Benjamini’s <a href="http://statweb.stanford.edu/~yuvalben/stat312/dataset_1/v1_locations.RData">website</a>.
<pre class="r"><code class="r"><span class="identifier">load</span><span class="paren">(</span><span class="string">"raw_data/v1_locations.RData"</span><span class="paren">)</span>
<span class="comment"># v1 locations</span>
<span class="identifier">dim</span><span class="paren">(</span><span class="identifier">v1_locations</span><span class="paren">)</span>
<span class="comment">## [1] 1331    3</span>
<span class="identifier">head</span><span class="paren">(</span><span class="identifier">v1_locations</span><span class="paren">)</span>
<span class="comment">##      [,1] [,2] [,3]</span>
<span class="comment">## [1,]   34   22    3</span>
<span class="comment">## [2,]   34   23    3</span>
<span class="comment">## [3,]   34   24    3</span>
<span class="comment">## [4,]   34   25    3</span>
<span class="comment">## [5,]   34   26    3</span>
<span class="comment">## [6,]   34   20    4</span></code></pre>
Note that <code>v1_locations</code> appears to hold the (x, y, z)-locations of each V1 voxel. However, recall that we had a number of voxels with mostly missing values. We remove these from our location data frame below.
<pre class="r"><code class="r"><span class="identifier">v1.locations</span> <span class="operator">&lt;-</span> <span class="identifier">as.data.frame</span><span class="paren">(</span><span class="identifier">v1_locations</span><span class="paren">[</span><span class="identifier">which</span><span class="paren">(</span><span class="identifier">missing.variables</span> <span class="operator">==</span> <span class="number">0</span><span class="paren">)</span>, <span class="paren">]</span><span class="paren">)</span>
<span class="identifier">colnames</span><span class="paren">(</span><span class="identifier">v1.locations</span><span class="paren">)</span> <span class="operator">&lt;-</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">"x"</span>, <span class="string">"y"</span>, <span class="string">"z"</span><span class="paren">)</span>
<span class="identifier">v1.locations</span><span class="operator">$</span><span class="identifier">cluster</span> <span class="operator">&lt;-</span> <span class="identifier">factor</span><span class="paren">(</span><span class="identifier">voxel.clusters</span><span class="paren">)</span>
<span class="identifier">rm</span><span class="paren">(</span><span class="identifier">v1_locations</span><span class="paren">)</span></code></pre>
Next, we can plot the voxels in space.
<pre class="r"><code class="r"><span class="keyword">library</span><span class="paren">(</span><span class="identifier">plotly</span><span class="paren">)</span>
<span class="identifier">voxel.clusters</span> <span class="operator">&lt;-</span> <span class="identifier">factor</span><span class="paren">(</span><span class="identifier">paste</span><span class="paren">(</span><span class="string">"cluster"</span>, <span class="identifier">voxel.clusters</span><span class="paren">)</span><span class="paren">)</span>
<span class="identifier">plot_ly</span><span class="paren">(</span><span class="identifier">v1.locations</span>, <span class="identifier">x</span> <span class="operator">=</span> <span class="operator">~</span><span class="identifier">x</span>, <span class="identifier">y</span> <span class="operator">=</span> <span class="operator">~</span><span class="identifier">y</span>, <span class="identifier">z</span> <span class="operator">=</span> <span class="operator">~</span><span class="identifier">z</span>, 
        <span class="identifier">color</span> <span class="operator">=</span> <span class="operator">~</span><span class="identifier">cluster</span>, 
        <span class="identifier">type</span> <span class="operator">=</span> <span class="string">"scatter3d"</span>,
        <span class="identifier">mode</span> <span class="operator">=</span> <span class="string">"markers"</span>,
        <span class="identifier">colors</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">'#e41a1c'</span>, <span class="string">'#377eb8'</span><span class="paren">)</span>,
        <span class="identifier">marker</span> <span class="operator">=</span> <span class="identifier">list</span><span class="paren">(</span><span class="identifier">line</span> <span class="operator">=</span> <span class="identifier">list</span><span class="paren">(</span><span class="identifier">color</span> <span class="operator">=</span> <span class="string">'black'</span>, <span class="identifier">width</span> <span class="operator">=</span> <span class="number">1.5</span><span class="paren">)</span><span class="paren">)</span><span class="paren">)</span> <span class="operator">%&gt;%</span>
  <span class="identifier">layout</span><span class="paren">(</span><span class="identifier">scene</span> <span class="operator">=</span> <span class="identifier">list</span><span class="paren">(</span><span class="identifier">xaxis</span> <span class="operator">=</span> <span class="identifier">list</span><span class="paren">(</span><span class="identifier">title</span> <span class="operator">=</span> <span class="string">'x'</span><span class="paren">)</span>,
                   <span class="identifier">yaxis</span> <span class="operator">=</span> <span class="identifier">list</span><span class="paren">(</span><span class="identifier">title</span> <span class="operator">=</span> <span class="string">'y'</span><span class="paren">)</span>,
                   <span class="identifier">zaxis</span> <span class="operator">=</span> <span class="identifier">list</span><span class="paren">(</span><span class="identifier">title</span> <span class="operator">=</span> <span class="string">'z'</span><span class="paren">)</span><span class="paren">)</span><span class="paren">)</span></code></pre>
&nbsp;
<pre class="r"><code class="r"><span class="keyword">library</span><span class="paren">(</span><span class="identifier">plotly</span><span class="paren">)</span>
<span class="identifier">voxel.clusters</span> <span class="operator">&lt;-</span> <span class="identifier">factor</span><span class="paren">(</span><span class="identifier">paste</span><span class="paren">(</span><span class="string">"cluster"</span>, <span class="identifier">voxel.clusters</span><span class="paren">)</span><span class="paren">)</span>
<span class="identifier">plot_ly</span><span class="paren">(</span><span class="identifier">v1.locations</span>, <span class="identifier">x</span> <span class="operator">=</span> <span class="operator">~</span><span class="identifier">x</span>, <span class="identifier">y</span> <span class="operator">=</span> <span class="operator">~</span><span class="identifier">y</span>, <span class="identifier">z</span> <span class="operator">=</span> <span class="operator">~</span><span class="identifier">z</span>, 
        <span class="identifier">color</span> <span class="operator">=</span> <span class="operator">~</span><span class="identifier">cluster</span>, 
        <span class="identifier">type</span> <span class="operator">=</span> <span class="string">"scatter3d"</span>,
        <span class="identifier">mode</span> <span class="operator">=</span> <span class="string">"markers"</span>,
        <span class="identifier">colors</span> <span class="operator">=</span> <span class="identifier">c</span><span class="paren">(</span><span class="string">'#e41a1c'</span>, <span class="string">'#377eb8'</span><span class="paren">)</span>,
        <span class="identifier">marker</span> <span class="operator">=</span> <span class="identifier">list</span><span class="paren">(</span><span class="identifier">line</span> <span class="operator">=</span> <span class="identifier">list</span><span class="paren">(</span><span class="identifier">color</span> <span class="operator">=</span> <span class="string">'black'</span>, <span class="identifier">width</span> <span class="operator">=</span> <span class="number">1.5</span><span class="paren">)</span><span class="paren">)</span><span class="paren">)</span> <span class="operator">%&gt;%</span>
  <span class="identifier">layout</span><span class="paren">(</span><span class="identifier">scene</span> <span class="operator">=</span> <span class="identifier">list</span><span class="paren">(</span><span class="identifier">xaxis</span> <span class="operator">=</span> <span class="identifier">list</span><span class="paren">(</span><span class="identifier">title</span> <span class="operator">=</span> <span class="string">'x'</span><span class="paren">)</span>,
                   <span class="identifier">yaxis</span> <span class="operator">=</span> <span class="identifier">list</span><span class="paren">(</span><span class="identifier">title</span> <span class="operator">=</span> <span class="string">'y'</span><span class="paren">)</span>,
                   <span class="identifier">zaxis</span> <span class="operator">=</span> <span class="identifier">list</span><span class="paren">(</span><span class="identifier">title</span> <span class="operator">=</span> <span class="string">'z'</span><span class="paren">)</span><span class="paren">)</span><span class="paren">)</span></code></pre>
&nbsp;

</div>
</div>

<div class="post-share"></div>

소스: <em><a href="https://rlbarter.github.io/superheat-examples/fMRI/">Superheat</a></em>