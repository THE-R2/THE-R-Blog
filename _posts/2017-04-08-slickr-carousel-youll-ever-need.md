---
ID: 1881
post_title: slickR – carousel you’ll ever need 
author: The-R
post_date: 2017-04-08 21:54:02
post_excerpt: ""
layout: post
permalink: >
  http://the-r.kr/2017/04/08/slickr-carousel-youll-ever-need/
published: true
avada_post_views_count:
  - "1"
scc_share_count_google+:
  - "0"
scc_share_count_facebook:
  - "-1"
scc_share_count_pocket:
  - "0"
scc_share_count_hatebu:
  - "0"
scc_share_count_crawldate:
  - 2017/04/09 22:33:42
scc_share_count_total:
  - "0"
inline_featured_image:
  - "0"
---
We are happy to bring the <a href="http://kenwheeler.github.io/slick/" target="_blank" rel="nofollow">slick</a> JavaScript library to R. It is self-described as “the last carousel you’ll ever need”. This carousel is based on putting the elements of the carousel in a <a href="https://www.w3schools.com/tags/tag_div.asp" target="_blank" rel="nofollow">div</a> HTML tag. This makes the carousel very versatile in what can be placed inside. Regular objects that are placed in a carousel can be for example: images, plots, tables, gifs, videos, iframes and even htmlwidgets.

<div class="figure"><img src="http://the-r.kr/wp-content/uploads/2017/04/slickRnestingWidgets.gif" width="456" height="284" data-lazy-loaded="true" /></div>

&nbsp;

This tool helps review multiple outputs in an efficient manner and saves much needed space in documents and Shiny applications, while creating a user friendly experience.

These carousels can be used directly from the R console, from RStudio, in Shiny apps and R Markdown documents.

<div id="installation" class="section level1">
<h1>Installation</h1>
<a href="https://cran.r-project.org/web/packages/slickR/index.html" target="_blank" rel="nofollow">CRAN</a>
<pre class="r"><code>install.packages('slickR')</code></pre>
<a href="https://github.com/metrumresearchgroup/slickR" target="_blank" rel="nofollow">Github</a> (dev)
<pre class="r"><code>devtools::install_github('metrumresearchgroup/slickR')</code></pre>
</div>

<div id="examples" class="section level1">
<h1>Examples</h1>
There are many options within the slick carousel, to get started with the basics we will show a few examples in the rest of the post. If you want to try out any of the examples you can go to this site where they are rendered and can be tested out.
<pre class="r"><code>
library(svglite)
library(lattice)
library(ggplot2)
library(rvest) 
library(reshape2)
library(dplyr)
library(htmlwidgets)
library(slickR)
</code></pre>
</div>

<div id="images" class="section level1">
<h1>Images</h1>
Some web scraping for the images example….
<pre class="r"><code>#NBA Team Logos
nbaTeams=c("ATL","BOS","BKN","CHA","CHI","CLE","DAL","DEN","DET","GSW",
    "HOU","IND","LAC","LAL","MEM","MIA","MIL","MIN","NOP","NYK",
    "OKC","ORL","PHI","PHX","POR","SAC","SAS","TOR","UTA","WAS")
teamImg=sprintf("https://i.cdn.turner.com/nba/nba/.element/img/4.0/global/logos/512x512/bg.white/svg/%s.svg",nbaTeams)

#Player Images
a1=read_html('http://www.espn.com/nba/depth')%&gt;%html_nodes(css = '#my-teams-table a')
a2=a1%&gt;%html_attr('href')
a3=a1%&gt;%html_text()
team_table=read_html('http://www.espn.com/nba/depth')%&gt;%html_table()
team_table=team_table[[1]][-c(1,2),]
playerTable=team_table%&gt;%melt(,id='X1')%&gt;%arrange(X1,variable)
playerName=a2[grepl('[0-9]',a2)]
playerId=do.call('rbind',lapply(strsplit(playerName,'[/]'),function(x) x[c(8,9)]))
playerId=playerId[playerId[,1]!='phi',]
playerTable$img=sprintf('http://a.espncdn.com/combiner/i?img=/i/headshots/nba/players/full/%s.png&amp;w=350&amp;h=254',playerId[,1])</code></pre>
<div id="simple-carousel" class="section level2">
<h2>Simple carousel</h2>
Let’s start easy: show the team logos one at a time with dots underneath
<pre class="r"><code>slickR(obj = teamImg,slideId = 'ex1',height = 100,width='100%')</code></pre>
<div class="figure"><img src="http://the-r.kr/wp-content/uploads/2017/04/ex1.gif" width="456" height="64" data-recalc-dims="1" data-lazy-loaded="true" /></div>
</div>
<div id="grouped-images" class="section level2">
<h2>Grouped Images</h2>
There are players on each team, so lets group the starting five together and have each dot correspond with a team:
<pre class="r"><code>slickR(
  obj = playerTable$img,
  slideId = c('ex2'),
  slickOpts = list(
    initialSlide = 0,
    slidesToShow = 5,
    slidesToScroll = 5,
    focusOnSelect = T,
    dots = T
  ),
  height = 100,width='100%'
)</code></pre>
<div class="figure"><img src="http://the-r.kr/wp-content/uploads/2017/04/ex2.gif" width="456" height="64" data-lazy-loaded="true" /></div>
</div>
<div id="replacing-the-dots" class="section level2">
<h2>Replacing the dots</h2>
Sometimes the dots won’t be informative enough so we can switch them with an HTML object, such as text or other images.
We can pass to the customPaging argument javascript code using the <code>htmlwidgets::JS</code> function.
<div id="replace-dots-with-text" class="section level2">
<h3>Replace dots with text</h3>
<pre class="r"><code>cP1=JS("function(slick,index) {return '&lt;a&gt;'+(index+1)+'&lt;/a&gt;';}")

slickR(
  obj = playerTable$img,
  slideId = 'ex3',
  dotObj = teamImg,
  slickOpts = list(
    initialSlide = 0,
    slidesToShow = 5,
    slidesToScroll = 5,
    focusOnSelect = T,
    dots = T,
    customPaging = cP1
  ),
  height=100,width='100%'
)</code></pre>
<div class="figure"><img src="http://the-r.kr/wp-content/uploads/2017/04/ex3.gif" width="456" height="64" data-lazy-loaded="true" /></div>
</div>
</div>
<div id="replace-dots-with-images" class="section level2">
<h3>Replace dots with Images</h3>
<pre class="r"><code>cP2=JS("function(slick,index) {return '&lt;a&gt;&lt;img src= ' + dotObj[index] + '  width=100% height=100%&gt;&lt;/a&gt;';}")


#Replace dots with Images
s1 &lt;- slickR(
  obj = playerTable$img,
  dotObj = teamImg,
  slickOpts = list(
    initialSlide = 0,
    slidesToShow = 5,
    slidesToScroll = 5,
    focusOnSelect = T,
    dots = T,
    customPaging = cP2
  ),height = 100,width='100%'
)

#Putting it all together in one slickR call
s2 &lt;- htmltools::tags$script(
  sprintf("var dotObj = %s", 
          jsonlite::toJSON(teamImg))
)

htmltools::browsable(htmltools::tagList(s2, s1))</code></pre>
<div class="figure"><img src="http://the-r.kr/wp-content/uploads/2017/04/ex7.gif" width="456" height="68" data-lazy-loaded="true" /></div>
</div>
</div>

<div id="plots" class="section level1">
<h1>Plots</h1>
To place plots directly into slickR we use svglite to convert a plot into svg code using xmlSVG and then convert it into a character object
<pre class="r"><code>plotsToSVG=list(
  #Standard Plot
    xmlSVG({plot(1:10)},standalone=TRUE),
  #lattice xyplot
    xmlSVG({print(xyplot(x~x,data.frame(x=1:10),type="l"))},standalone=TRUE),
  #ggplot
    xmlSVG({show(ggplot(iris,aes(x=Sepal.Length,y=Sepal.Width,colour=Species))+
                   geom_point())},standalone=TRUE), 
  #lattice dotplot
    xmlSVG({print(dotplot(variety ~ yield | site , data = barley, groups = year,
                          key = simpleKey(levels(barley$year), space = "right"),
                          xlab = "Barley Yield (bushels/acre) ",
                          aspect=0.5, layout = c(1,6), ylab=NULL))
            },standalone=TRUE) 
)

#make the plot self contained SVG to pass into slickR 
s.in=sapply(plotsToSVG,function(sv){paste0("data:image/svg+xml;utf8,",as.character(sv))})</code></pre>
<pre class="r"><code>slickR(s.in,slideId = 'ex4',slickOpts = list(dots=T), height = 200,width = '100%')</code></pre>
<div class="figure"><img src="http://the-r.kr/wp-content/uploads/2017/04/ex4.gif" width="456" height="109" data-lazy-loaded="true" /></div>
<div id="synching-carousels" class="section level2">
<h2>Synching Carousels</h2>
There are instances when you have many outputs at once and do not want to go through all, so you can combine two carousels one for viewing and one for searching.
<pre class="r"><code>slickR(rep(s.in,each=5),slideId = c('ex5up','ex5down'),
       slideIdx = list(1:20,1:20),
       synchSlides = c('ex5up','ex5down'),
       slideType = rep('img',4),
       slickOpts = list(list(slidesToShow=1,slidesToScroll=1),
                        list(dots=F,slidesToScroll=1,slidesToShow=5,
                             centerMode=T,focusOnSelect=T)
                        ),
       height=100,width = '100%'
       )</code></pre>
<div class="figure"><img src="http://the-r.kr/wp-content/uploads/2017/04/ex5.gif" width="456" height="109" data-lazy-loaded="true" /></div>
</div>
</div>

<div id="iframes" class="section level1">
<h1>Iframes</h1>
Since the carousel can accept any html element we can place iframes in the carousel.
There are times when you may want to put in different DOMs rather than an image in slick. Using slideType you can specify which DOM is used in the slides.
For example let’s put the help Rd files from ggplot2 into a slider using the helper function getHelp. (Dont forget to open the output to a browser to view the iframe contents).
<pre class="r"><code>geom_filenames=ls("package:ggplot2",pattern = '^geom')

slickR(unlist(lapply(geom_filenames,getHelp,pkg = 'ggplot2')),slideId = 'ex6',slideType = 'iframe',height = '400px',width='100%',slickOpts = list(dots=T,slidesToShow=2,slidesToScroll=2))</code></pre>
<div class="figure"><img src="http://the-r.kr/wp-content/uploads/2017/04/ex6.gif" width="456" height="217" data-lazy-loaded="true" /></div>
<div id="htmlwidgets" class="section level2">
<h2>htmlwidgets</h2>
Finally, we can really leverage R and place self contained htmlwidgets in iframes (like leaflets and plotly) and use them in a carousel. This solves a problem of how to run many htmlwidgets at once outside of Shiny.
<pre class="r"><code>library(leaflet)
library(plotly)

l &lt;- leaflet() %&gt;% addTiles()
htmlwidgets::saveWidget(l,'leaflet.html')

p &lt;- iris%&gt;%ggplot(aes(x=Sepal.Length,y=Sepal.Width))+geom_point()
pL= ggplotly(p)
htmlwidgets::saveWidget(pL,'ggplotly.html')

slickR(c(rep(paste0(readLines('leaflet.html'),collapse='\n'),4),
         rep(paste0(readLines('ggplotly.html'),collapse='\n'),4)),
       slideId = c('leaf','plot'),
       slideIdx = list(1:4,5:8),
       slideType = rep('iframe',2),
       slickOpts = list(list(dots=T,slidesToShow=2,slidesToScroll=2),
                        list(dots=T,slidesToShow=2,slidesToScroll=2)),
       height='200px',width='100%')</code></pre>
<div class="figure"><img src="http://the-r.kr/wp-content/uploads/2017/04/slickRnestingWidgets.gif" width="456" height="284" data-lazy-loaded="true" /></div>
</div>
</div>

<hr />

<em>Jonathan Sidi joined Metrum Research Group in 2016 after working for several years on problems in applied statistics, financial stress testing and economic forecasting in both industrial and academic settings. To learn more about additional open-source software packages developed by Metrum Research Group please visit the Metrum <a href="http://metrumrg.com/opensourcetools.html" target="_blank" rel="nofollow">website</a>. Contact: For questions and comments, feel free to email me at: yonis@metrumrg.com or open an issue for bug fixes or enhancements at <a href="https://github.com/metrumresearchgroup/ggedit/issues" target="_blank" rel="nofollow">github</a>.</em>

소스: <em><a href="https://www.r-bloggers.com/slickr/">slickR – the last carousel you’ll ever need | R-bloggers</a></em>