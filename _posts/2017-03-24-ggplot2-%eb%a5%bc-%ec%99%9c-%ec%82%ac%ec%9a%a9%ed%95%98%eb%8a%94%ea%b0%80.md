---
ID: 1761
post_title: ggplot2 를 왜 사용하는가?
author: The-R
post_date: 2017-03-24 13:23:51
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/03/24/ggplot2-%eb%a5%bc-%ec%99%9c-%ec%82%ac%ec%9a%a9%ed%95%98%eb%8a%94%ea%b0%80/'
published: true
inline_featured_image:
  - "0"
---
많은 R 사용자들은 시각화를 위해 Hadley Wickham이 개발한 ggplot2 패키지를 대부분 사용할 것입니다. 물론 많은 분들이 동의하는건 아니겠지만...
<blockquote>…one place I lose tons of street cred in the data science community is when I talk about ggplot2… ggplot2 is an R package/phenomenon for data visualization. It was created by Hadley Wickham, who is (in my opinion) perhaps the most important statistician/data scientist on the planet. It is one of the best maintained, most important, and really well done R packages. Hadley also supports R software like few other people on the planet.</blockquote>
<blockquote>But I don’t use ggplot2 and I get nervous when other people do.</blockquote>
Jeff is a great statistician, an excellent and experienced educator, and among my favorite scientific communicators. He and I agree strongly on a wide variety number of topics, ranging from <a href="http://simplystatistics.org/2013/10/23/the-leek-group-guide-to-reviewing-scientific-papers/" target="_blank" rel="nofollow">peer review</a> to <a href="http://simplystatistics.org/2014/02/14/on-the-scalability-of-statistical-procedures-why-the-p-value-bashers-just-dont-get-it/" target="_blank" rel="nofollow">p-values</a>.

In short, I’ve learned a lot from him. So I appreciate the chance to return the favor. I’m going to try crossing this one last disagreement off the list.
<h3 id="where-base-plotting-is-better">Where base plotting is better</h3>
I’ll start by giving credit: there are plenty of cases that base plotting tools are superior. The tools were developed over many years by very smart people. While some methods haven’t stood the test of time, others have.

As one example (which Jeff brings up in his post), take <em>clustered heatmaps</em>. Heatmaps are in fact easy to make in ggplot2 with <code class="highlighter-rouge">geom_tile</code> or <code class="highlighter-rouge">geom_raster</code>, but not with row- and column-clustering built-in, which is essential in applications such as genomics. You’ll see that I use a base-plotting heatmap <a href="http://varianceexplained.org/r/love-actually-network/" target="_blank" rel="nofollow">in my “Love Actually” post</a>, as well as a base-plotted dendrogram.<sup id="fnref:heatmap2"><a class="footnote" href="http://varianceexplained.org/r/why-I-use-ggplot2/#fn:heatmap2" target="_blank" rel="nofollow">1</a></sup>

But it’s worth noting that in many cases, ggplot2 extensions have sprung up even to replace those areas where base plotting had an advantage. For example, plotting networks used to be base R’s territory, led by plotting methods in the <a href="http://igraph.org/redirect.html" target="_blank" rel="nofollow">igraph package</a>. But I recently started using the <a href="https://github.com/thomasp85/ggraph" target="_blank" rel="nofollow">ggraph</a> package and been blown away by how much easier it is to control visual aesthetics of a network.
<h3 id="is-base-r-better-for-quick-exploratory-plots">Is base R better for quick, exploratory plots?</h3>
Jeff:
<blockquote>Exploratory graphs don’t have to be pretty. I’m going to be the only one who looks at 99% of them. But I have to be able to make them quickly and I have to be able to make a broad range of plots with minimal code… The flexibility of base R comes at a price, but it means you can make all sorts of things you need to without struggling against the system.</blockquote>
First of all, having exploratory plots be pretty, even if it’s not necessary, is clearly a bonus. My exploratory analyses aren’t publication ready, but they’re <em>definitely</em> ready to send to a colleague or to share on my company’s internal chat.

But in any case, when making quick, exploratory graphs, I find using base R <em>absolutely</em> involves struggling against the system. I’ll give three examples, though they’re far from unique.
<ul>
 	<li><strong>Creating legends.</strong> Any time you use colors, shapes, transparency, etc in base plotting, you need to specify the mappings in the legend yourself, while ggplot2 generates it for you. For me, this is simply a no-brainer, and Jeff agress that “ggplot2 crushes base R for simplicity” when working with, for example, a color scale.

Building your own legend slows down exploratory analysis in two ways. First, time spent specifying legends is time and attention you’re not putting towards your data and your scientific question. Second, it introduces room for error, like an off-by-one or transposition in your legend colors. These are dangerous when you’re working quickly and not proofreading.</li>
 	<li><strong>Grouped lines</strong>: If I want to show, say, the price of six stocks or the expression level of six genes over time, I probably want to show them as six line plots. In ggplot2, you add a <code class="highlighter-rouge">group = stock</code> or <code class="highlighter-rouge">group = gene</code> aesthetic. In base plotting, you write a loop, subset the data each time, and call <code class="highlighter-rouge">lines</code>– but you’ll have to have created a blank plot beforehand with the appropriate axes.<sup id="fnref:matplot"><a class="footnote" href="http://varianceexplained.org/r/why-I-use-ggplot2/#fn:matplot" target="_blank" rel="nofollow">2</a></sup></li>
 	<li><strong>Faceting</strong> (creating a subplot for each subset of your data) is one of the primary tools I use when constructing a plot- it’s another way to spot relationships. In base R you’d have to construct each plot in a loop.</li>
</ul>
The fact that graphs are “quick-and-dirty” doesn’t mean that these features stop being useful. In the next section I show a plot I made as part of an exploratory analysis that needs all three.

I’m not sure that base R plotters even realize how powerful and important legends, faceting and grouping are in exploratory analysis, simply because they’re so painful that they never become a habit. If adding a legend takes effort, you may think it’s natural in exploratory plotting to keep looking back to the code to check which color means what. If faceting is challenging, you might lean towards use other aesthetics such as shape (making a plot more crowded), or to look only at one facet at a time. This loses out on potential conclusions you could make in your exploratory analysis.

To paraphrase Wayne Gretzky, <strong>“you miss 100% of the plots you don’t make.”</strong>
<h3 id="are-ggplot2-and-base-plotting-equally-easy">Are ggplot2 and base plotting equally easy?</h3>
By way of showing how ggplot2 and base plotting are about equally easy, Jeff makes a comparison between two Tufte-style bar plots. Since they use about the same amount of code, he argues:
<blockquote>This is one where neither system is particularly better, but the time-optimal solution is to stick with whichever system you learned first.</blockquote>
This particular comparison is stacking the deck in a few ways.
<ul>
 	<li>It’s a simple bar plot plotted from a named vector. This is a special case for the <code class="highlighter-rouge">barplot</code> object.</li>
 	<li>It also has a large amount of customization for a very specific theme.<sup id="fnref:theme"><a class="footnote" href="http://varianceexplained.org/r/why-I-use-ggplot2/#fn:theme" target="_blank" rel="nofollow">3</a></sup></li>
</ul>
Let’s instead try a figure I ran into during one of my own analyses, from <a href="http://varianceexplained.org/r/tidy-genomics-broom/" target="_blank" rel="nofollow">this blog post about tidying</a>. A quick setup just to show where it comes from:
<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="c1"># bit of setup
</span><span class="n">library</span><span class="p">(</span><span class="n">ggplot2</span><span class="p">)</span>
<span class="n">library</span><span class="p">(</span><span class="n">dplyr</span><span class="p">)</span>

<span class="n">load</span><span class="p">(</span><span class="n">url</span><span class="p">(</span><span class="s2">"http://varianceexplained.org/files/ggplot2_example.rda"</span><span class="p">))</span>
<span class="n">top_data</span> <span class="o">&lt;-</span> <span class="n">cleaned_data</span> <span class="o">%&gt;%</span>
    <span class="n">semi_join</span><span class="p">(</span><span class="n">top_intercept</span><span class="p">,</span> <span class="n">by</span> <span class="o">=</span> <span class="s2">"systematic_name"</span><span class="p">)</span></code></pre>
</figure>
I want to compare expression by growth rate in twenty genes in six conditions, the kind of analysis I did many times in that and <a href="http://varianceexplained.org/r/tidy-genomics/" target="_blank" rel="nofollow">the previous post</a>. Here’s how I’d make such a figure in ggplot2:
<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">ggplot</span><span class="p">(</span><span class="n">top_data</span><span class="p">,</span> <span class="n">aes</span><span class="p">(</span><span class="n">rate</span><span class="p">,</span> <span class="n">expression</span><span class="p">,</span> <span class="n">color</span> <span class="o">=</span> <span class="n">nutrient</span><span class="p">))</span> <span class="o">+</span>
    <span class="n">geom_point</span><span class="p">()</span> <span class="o">+</span>
    <span class="n">geom_smooth</span><span class="p">(</span><span class="n">method</span> <span class="o">=</span> <span class="s2">"lm"</span><span class="p">,</span> <span class="n">se</span> <span class="o">=</span> <span class="n">FALSE</span><span class="p">)</span> <span class="o">+</span>
    <span class="n">facet_wrap</span><span class="p">(</span><span class="o">~</span><span class="n">name</span> <span class="o">+</span> <span class="n">systematic_name</span><span class="p">,</span> <span class="n">scales</span> <span class="o">=</span> <span class="s2">"free_y"</span><span class="p">)</span></code></pre>
</figure>
<img src="http://the-r.kr/wp-content/uploads/2017/03/unnamed-chunk-1-1-1.png" alt="center" width="456" height="456" data-lazy-loaded="true" />

Now, here’s what a rough equivalent looks like in base R:
<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">par</span><span class="p">(</span><span class="n">mar</span> <span class="o">=</span> <span class="n">c</span><span class="p">(</span><span class="m">1.5</span><span class="p">,</span> <span class="m">1.5</span><span class="p">,</span> <span class="m">1.5</span><span class="p">,</span> <span class="m">1.5</span><span class="p">))</span>

<span class="n">colors</span> <span class="o">&lt;-</span> <span class="m">1</span><span class="o">:</span><span class="m">6</span>
<span class="n">names</span><span class="p">(</span><span class="n">colors</span><span class="p">)</span> <span class="o">&lt;-</span> <span class="n">unique</span><span class="p">(</span><span class="n">top_data</span><span class="o">$</span><span class="n">nutrient</span><span class="p">)</span>

<span class="c1"># legend approach from http://stackoverflow.com/a/10391001/712603
</span><span class="n">m</span> <span class="o">&lt;-</span> <span class="n">matrix</span><span class="p">(</span><span class="n">c</span><span class="p">(</span><span class="m">1</span><span class="o">:</span><span class="m">20</span><span class="p">,</span> <span class="m">21</span><span class="p">,</span> <span class="m">21</span><span class="p">,</span> <span class="m">21</span><span class="p">,</span> <span class="m">21</span><span class="p">),</span> <span class="n">nrow</span> <span class="o">=</span> <span class="m">6</span><span class="p">,</span> <span class="n">ncol</span> <span class="o">=</span> <span class="m">4</span><span class="p">,</span> <span class="n">byrow</span> <span class="o">=</span> <span class="n">TRUE</span><span class="p">)</span>
<span class="n">layout</span><span class="p">(</span><span class="n">mat</span> <span class="o">=</span> <span class="n">m</span><span class="p">,</span> <span class="n">heights</span> <span class="o">=</span> <span class="n">c</span><span class="p">(</span><span class="m">.18</span><span class="p">,</span> <span class="m">.18</span><span class="p">,</span> <span class="m">.18</span><span class="p">,</span> <span class="m">.18</span><span class="p">,</span> <span class="m">.18</span><span class="p">,</span> <span class="m">.1</span><span class="p">))</span>

<span class="n">top_data</span><span class="o">$</span><span class="n">combined</span> <span class="o">&lt;-</span> <span class="n">paste</span><span class="p">(</span><span class="n">top_data</span><span class="o">$</span><span class="n">name</span><span class="p">,</span> <span class="n">top_data</span><span class="o">$</span><span class="n">systematic_name</span><span class="p">)</span>
<span class="k">for</span> <span class="p">(</span><span class="n">gene</span> <span class="k">in</span> <span class="n">unique</span><span class="p">(</span><span class="n">top_data</span><span class="o">$</span><span class="n">combined</span><span class="p">))</span> <span class="p">{</span>
    <span class="n">sub_data</span> <span class="o">&lt;-</span> <span class="n">filter</span><span class="p">(</span><span class="n">top_data</span><span class="p">,</span> <span class="n">combined</span> <span class="o">==</span> <span class="n">gene</span><span class="p">)</span>
    <span class="n">plot</span><span class="p">(</span><span class="n">expression</span> <span class="o">~</span> <span class="n">rate</span><span class="p">,</span> <span class="n">sub_data</span><span class="p">,</span> <span class="n">col</span> <span class="o">=</span> <span class="n">colors</span><span class="p">[</span><span class="n">sub_data</span><span class="o">$</span><span class="n">nutrient</span><span class="p">],</span> <span class="n">main</span> <span class="o">=</span> <span class="n">gene</span><span class="p">)</span>
    <span class="k">for</span> <span class="p">(</span><span class="n">n</span> <span class="k">in</span> <span class="n">unique</span><span class="p">(</span><span class="n">sub_data</span><span class="o">$</span><span class="n">nutrient</span><span class="p">))</span> <span class="p">{</span>
        <span class="n">m</span> <span class="o">&lt;-</span> <span class="n">lm</span><span class="p">(</span><span class="n">expression</span> <span class="o">~</span> <span class="n">rate</span><span class="p">,</span> <span class="n">filter</span><span class="p">(</span><span class="n">sub_data</span><span class="p">,</span> <span class="n">nutrient</span> <span class="o">==</span> <span class="n">n</span><span class="p">))</span>
        <span class="k">if</span> <span class="p">(</span><span class="o">!</span><span class="n">is.na</span><span class="p">(</span><span class="n">m</span><span class="o">$</span><span class="n">coefficients</span><span class="p">[</span><span class="m">2</span><span class="p">]))</span> <span class="p">{</span>
            <span class="n">abline</span><span class="p">(</span><span class="n">m</span><span class="p">,</span> <span class="n">col</span> <span class="o">=</span> <span class="n">colors</span><span class="p">[</span><span class="n">n</span><span class="p">])</span>
        <span class="p">}</span>
    <span class="p">}</span>
<span class="p">}</span>

<span class="c1"># create a new plot for legend
</span><span class="n">plot</span><span class="p">(</span><span class="m">1</span><span class="p">,</span> <span class="n">type</span> <span class="o">=</span> <span class="s2">"n"</span><span class="p">,</span> <span class="n">axes</span> <span class="o">=</span> <span class="n">FALSE</span><span class="p">,</span> <span class="n">xlab</span> <span class="o">=</span> <span class="s2">""</span><span class="p">,</span> <span class="n">ylab</span> <span class="o">=</span> <span class="s2">""</span><span class="p">)</span>
<span class="n">legend</span><span class="p">(</span><span class="s2">"top"</span><span class="p">,</span> <span class="n">names</span><span class="p">(</span><span class="n">colors</span><span class="p">),</span> <span class="n">col</span> <span class="o">=</span> <span class="n">colors</span><span class="p">,</span> <span class="n">horiz</span> <span class="o">=</span> <span class="n">TRUE</span><span class="p">,</span> <span class="n">lwd</span> <span class="o">=</span> <span class="m">4</span><span class="p">)</span></code></pre>
</figure>
<img src="http://the-r.kr/wp-content/uploads/2017/03/unnamed-chunk-2-1-1.png" alt="center" width="456" height="456" data-lazy-loaded="true" />

That’s something like 5x as much code, and the bulk comes at the pain points I discussed earlier: adding a legend, faceting, and grouping. And even with that difference, the ggplot2 version is <em>still</em> closer to being publication-ready. (The main thing to be fixed is the labels and facet titles).

But counting lines of code is not the point. The point is that when you’re building a base plot, you’re thinking about:
<ul>
 	<li><strong>programming logic</strong>: There’s two nested loops and an if statement, dealing with issues like subsets of subsets of your data, and checking that each regression had enough points to fit a line.</li>
 	<li><strong>graphics devices</strong>: If you don’t reset the margins first with <code class="highlighter-rouge">par</code>, the plots aren’t going to fit. You have to initialize a new empty plot just to add the legend in its own space, not to mention that mess of a <code class="highlighter-rouge">layout</code> function. (Does anyone know a better way?)</li>
</ul>
As a result, here’s a few things you’re <strong>not</strong> thinking about:
<ul>
 	<li><strong>Plotting choices</strong>: You had to have decided on those choices right away. If you decide you wanted 30 genes instead of 20, or that you’re going to facet on nutrient instead of gene, you’re doing some rewriting. Whereas that exact same ggplot2 code will work on 1 gene or on 50 (try it!).</li>
 	<li><strong>Your scientific question</strong>: Talk about getting taken out of the flow. When you get a <code class="highlighter-rouge">figure margins too large</code> error because you’re trying to plot too many genes at once and start adjusting <code class="highlighter-rouge">par</code> arguments, you’re certainly not focusing on what those genes represent.</li>
</ul>
This is <em>not</em> an isolated case. I use faceting in a substantial portion of my plots, and legends in the vast majority. And while I’m out of practice with base plotting, I don’t think my base R solution was unusual. I’d challenge base R users to come up with a plot of the above <code class="highlighter-rouge">top_data</code> that doesn’t involve as much hassle, and that is as informative as the above ggplot2 plot.
<h3 id="is-ggplot2-too-pretty-and-easy-to-use">Is ggplot2 too pretty and easy to use?</h3>
Jeff shows an example of a ggplot2 graph, and argues:
<blockquote>What often happens with students in a first serious data analysis class is they think that plot is done. But it isn’t even close. Here are a few things you would need to do to make this plot production ready: (1) make the axes bigger, (2) make the labels bigger, (3) make the labels be full names (latitude and longitude, ideally with units when variables need them), (4) make the legend title be number of stations reporting…. a very common move by a person who knows a little R/data analysis would be to leave that graph as it is and submit it directly….</blockquote>
<blockquote><strong>The one nice thing about teaching base R here is that the base version for this plot is either (a) a ton of work or (b) ugly.</strong> In either case, it makes the student think very hard about what they need to do to make the plot better, rather than just assuming it is ok.</blockquote>
Here Jeff explicitly argues that ugliness and difficulty-of-use are features, not bugs.

I really didn’t set out to make fun of Jeff, but in this case it was a bit hard to resist.
<div class="SandboxRoot env-bp-350" data-twitter-event-id="0">
<div id="twitter-widget-0" class="EmbeddedTweet EmbeddedTweet--mediaForward media-forward js-clickToOpenTarget js-tweetIdInfo" lang="en" data-click-to-open-target="https://twitter.com/drob/status/697858212779806721" data-iframe-title="Twitter Tweet" data-dt-full="%{hours12}:%{minutes} %{amPm} - %{day} %{month} %{year}" data-dt-months="Jan|Feb|Mar|Apr|May|Jun|Jul|Aug|Sep|Oct|Nov|Dec" data-dt-am="AM" data-dt-pm="PM" data-dt-now="now" data-dt-s="s" data-dt-m="m" data-dt-h="h" data-dt-second="second" data-dt-seconds="seconds" data-dt-minute="minute" data-dt-minutes="minutes" data-dt-hour="hour" data-dt-hours="hours" data-dt-abbr="%{number}%{symbol}" data-dt-short="%{day} %{month}" data-dt-long="%{day} %{month} %{year}" data-scribe="page:tweet" data-tweet-id="697858212779806721" data-twitter-event-id="1"><article class="MediaCard
           MediaCard--mediaForward

           customisable-border" dir="ltr" data-scribe="component:card">
<div class="MediaCard-media"><a class="MediaCard-borderOverlay" tabindex="-1" title="View image on Twitter" href="https://twitter.com/drob/status/697858212779806721/photo/1"><span class="u-hiddenVisually">View image on Twitter</span></a>
<div class="MediaCard-widthConstraint js-cspForcedStyle" data-style="max-width: 139px">
<div class="MediaCard-mediaContainer js-cspForcedStyle" data-style="padding-bottom: 133.0935%"><a class="MediaCard-mediaAsset
                    NaturalImage
" href="https://twitter.com/drob/status/697858212779806721/photo/1" data-scribe="element:photo"><img class="NaturalImage-image" title="View image on Twitter" src="https://pbs.twimg.com/media/Ca9KWL5UAAAI4sj.jpg:small" alt="View image on Twitter" width="139" height="185" data-srcset="https%3A%2F%2Fpbs.twimg.com%2Fmedia%2FCa9KWL5UAAAI4sj.jpg%3Asmall 139w,https%3A%2F%2Fpbs.twimg.com%2Fmedia%2FCa9KWL5UAAAI4sj.jpg%3Alarge 139w,https%3A%2F%2Fpbs.twimg.com%2Fmedia%2FCa9KWL5UAAAI4sj.jpg 139w" /></a></div>
</div>
</div>
</article>
<div class="EmbeddedTweet-tweet">
<blockquote class="Tweet h-entry js-tweetIdInfo subject expanded
                   is-deciderHtmlWhitespace" cite="https://twitter.com/drob/status/697858212779806721" data-tweet-id="697858212779806721" data-scribe="section:subject">
<div class="Tweet-header u-cf">
<div class="Tweet-brand u-floatRight">
<div class="Icon Icon--twitter " title=""></div>
<span class="u-hiddenInNarrowEnv"><a class="FollowButton follow-button profile" title="Follow David Robinson on Twitter" href="https://twitter.com/drob" data-scribe="component:followbutton">Follow</a></span></div>
<div class="TweetAuthor " data-scribe="component:author"><a class="TweetAuthor-link Identity u-linkBlend" href="https://twitter.com/drob" data-scribe="element:user_link"><span class="TweetAuthor-avatar Identity-avatar"><img class="Avatar" src="http://the-r.kr/wp-content/uploads/2017/03/David_Robinson_bigger.jpg" alt="" data-scribe="element:avatar" data-src-2x="http://the-r.kr/wp-content/uploads/2017/03/David_Robinson_bigger.jpg" data-src-1x="https://pbs.twimg.com/profile_images/777175344/David_Robinson_normal.jpg" /></span><span class="TweetAuthor-name Identity-name customisable-highlight" title="David Robinson" data-scribe="element:name">David Robinson</span> <span class="TweetAuthor-screenName Identity-screenName" dir="ltr" title="@drob" data-scribe="element:screen_name">@drob</span></a></div>
</div>
<div class="Tweet-body e-entry-content" data-scribe="component:tweet">
<p class="Tweet-text e-entry-title" dir="ltr" lang="en">Short version of why <a class="PrettyLink profile customisable h-card" dir="ltr" href="https://twitter.com/jtleek" data-mentioned-user-id="176883031" data-scribe="element:mention"><span class="PrettyLink-prefix">@</span><span class="PrettyLink-value">jtleek</span></a> uses base plotting instead of ggplot2:<a class="link customisable" dir="ltr" title="http://simplystatistics.org/2016/02/11/why-i-dont-use-ggplot2/" href="https://t.co/gUQvhEsjWv" target="_blank" rel="nofollow noopener" data-expanded-url="http://simplystatistics.org/2016/02/11/why-i-dont-use-ggplot2/" data-scribe="element:url"><span class="u-hiddenVisually">http://</span>simplystatistics.org/2016/02/11/why<span class="u-hiddenVisually">-i-dont-use-ggplot2/ </span>…</a> <a class="PrettyLink hashtag customisable" dir="ltr" href="https://twitter.com/hashtag/rstats?src=hash" rel="tag" data-query-source="hashtag_click" data-scribe="element:hashtag"><span class="PrettyLink-prefix">#</span><span class="PrettyLink-value">rstats</span></a></p>

<div class="Tweet-metadata dateline"><a class="u-linkBlend u-url customisable-highlight long-permalink" href="https://twitter.com/drob/status/697858212779806721" data-datetime="2016-02-11T19:02:18+0000" data-scribe="element:full_timestamp"><time class="dt-updated" title="Time posted: 11 Feb 2016, 19:02:18 (UTC)" datetime="2016-02-11T19:02:18+0000">4:02 AM - 12 Feb 2016</time></a></div>
<ul class="Tweet-actions" data-scribe="component:actions">
 	<li class="Tweet-action">
<div class="Icon Icon--reply TweetAction-icon" title="Reply"></div></li>
 	<li class="Tweet-action">
<div class="Icon Icon--retweet TweetAction-icon" title="Retweet"></div>
<a class="TweetAction TweetAction--retweet web-intent" href="https://twitter.com/intent/retweet?tweet_id=697858212779806721" data-scribe="element:retweet"><span class="TweetAction-stat" data-scribe="element:retweet_count">22</span><span class="u-hiddenVisually">22 Retweets</span></a></li>
 	<li class="Tweet-action">
<div class="Icon Icon--heart TweetAction-icon" title="Like"></div>
<a class="TweetAction TweetAction--heart web-intent" href="https://twitter.com/intent/like?tweet_id=697858212779806721" data-scribe="element:heart"><span class="TweetAction-stat" data-scribe="element:heart_count">62</span><span class="u-hiddenVisually">62 likes</span></a></li>
</ul>
</div></blockquote>
</div>
</div>
<div class="resize-sensor"></div>
</div>
But here I’ll address the substance. For one thing, I don’t think the example he presents is a particularly convincing one: as <a href="http://simplystatistics.org/2016/02/11/why-i-dont-use-ggplot2/#comment-2508952644" target="_blank" rel="nofollow">Ben Moore</a> notes, issues (1) and (2) are entirely the consequence of Jeff plotting the figure at a large size then scaling it down, and issues (3) and (4) are solvable with <code class="highlighter-rouge">+ labs(x = "Latitude", y = "Longitude", color = "# of stations")</code>. But I understand it as a theoretical possibility. If your defaults are too good, you might not be inspired to improve them.

But Jeff is presenting a false dichotomy between <strong>“Get a pretty good plot in ggplot2, submit it immediately,”</strong> and <strong>“Get an ugly plot in base R, spend time to make it into a great plot”</strong>. Here are other possibilities I’d argue are far more relevant:
<ul>
 	<li><strong>Someone gets an ugly graph in base R, sticks with it</strong>. I used to teach base plotting to beginners (<a href="http://varianceexplained.org/r/teach_ggplot2_to_beginners" target="_blank" rel="nofollow">not anymore!</a>) and I can tell you that having ugly output does <em>not</em> stop people from thinking they’re finished. Even if they do add a color scale, there’s no reason to believe they’ll follow it by fixing the x- and y- axis labels. Putting more energy into one part of your plot doesn’t make you put more energy in everywhere.

Indeed, it should be pretty clear that having ugly plots by default is more likely to <em>hurt</em> your goal of spreading good graphing practices, because it sets a poor example for the user (the <a href="https://en.wikipedia.org/wiki/Broken_windows_theory" target="_blank" rel="nofollow">“broken window” effect</a>). Jeff can recognize problems in a plot because he has years of experience in data visualization. If the first R plots a student sees are ugly, he’s not going to spontaneously strive towards beauty. If every plot starts without a legend, he’s going to start thinking of legends as optional.</li>
 	<li><strong>Someone gets a pretty good plot in ggplot2, and uses the saved time making it great.</strong> You’re getting a head start! Comparing base R used perfectly to ggplot2 used sloppily is unfair.</li>
 	<li><strong>Someone gets a pretty good plot in ggplot2, then discards it or iterates on it.</strong> There’s nothing quite as dreadful as spending twenty minutes building a plot only to realize it doesn’t communicate what you want. It’s easier to try multiple if each one is less effort, and if each result is pretty close to the final version. For instance, suppose you discovered that there’s nothing informative to be gained from a color scale. In ggplot2 you’d know that immediately, while in base plotting you’ll first have to go through the effort of adding one.</li>
 	<li><strong>Someone gets a pretty good plot in ggplot2, and that’s enough for their current purpose.</strong> I’ve submitted plenty of ggplot2 figures in assignments and manuscripts. But I also use ggplot2 for tweeting, blogging, or for sharing preliminary work with with colleagues and coworkers. For those, having an x-axis named “lat” instead of “latitude” is no big deal- but not having a legend would be completely unacceptable.</li>
</ul>
There’s one particular danger I’d argue is an order of magnitude more common and more dangerous than all the others.
<ul>
 	<li><strong>Someone discovers that making a basic plot in R is a ton of work, gives up, goes back to Excel.</strong> It’s pleasant to imagine that people start an R course thinking “Whatever it takes, I will make publication-quality figures in R.” Then, any challenge along the way is a valuable learning experience for them: they’ll spend the time to get their legend perfect, and at the end they’ll <em>appreciate</em> that legend, because by golly they worked for it!

But the truth is we have limited educational bandwidth to spend. If making a good plot takes a lot of effort, people will leave the course with a negative impression of R, and they won’t bother learning more. I made this point in my original <a href="http://varianceexplained.org/r/teach_ggplot2_to_beginners/" target="_blank" rel="nofollow">“teach ggplot2 to beginners” post</a>:</li>
</ul>
<blockquote>Why does it matter how the plot looks? <strong>Because you’re not just teaching students <em>how</em> to program in R, you’re teaching them that they <em>should.</em></strong> Learning to program takes effort and investment, and the more compelling the figures you can create very early in the course, the more easily you can convince them it is worth the effort.</blockquote>
In fact, going back to Excel isn’t the worst case: the worst case is that they stop bothering with data visualizations altogether. And when they think of graphs as either <strong>“(a) a ton of work or (b) ugly”</strong>, who could blame them?
<h3 id="why-i-use-ggplot2">Why I use ggplot2</h3>
I originally titled this post “Why I don’t use base R plotting.” But I realized that, appearances to the contrary, I don’t actually want to talk about what’s bad about base plotting, I want to talk about what’s so great about ggplot2. (To say the least, ggplot2 does not need my defense, but I’d still like to share. This isn’t a polemic, it’s a gospel).

To Jeff, the difference between base R and ggplot2 is just a difference between one bag of tricks and another:
<blockquote>…I learned all the stupid little tricks for that system, it was a huge pain, and it would be a huge pain to learn it again for ggplot2, to make very similar types of plots.</blockquote>
Base R plotting is indeed a bag of tricks. They’re often great tricks (especially for their time, and relative to what came before!). But why does <code class="highlighter-rouge">plot</code> expect one row per observation, while <code class="highlighter-rouge">matplot</code> expects one column per group? Because they’re two different ways to build two different plots. Why do you call <code class="highlighter-rouge">plot(..., type = "l")</code> to add the first line to a graph, then <code class="highlighter-rouge">lines</code> to add each additional one? Because that’s what those two different tricks are for.

So to Jeff, faceting, color scales, legends, and all the things that made the above example shorter are useful tricks that ggplot2 has that that base R doesn’t. They’re “points scored” in the ggplot2 column.

But ggplot2 isn’t a bag of tricks.

<img src="http://the-r.kr/wp-content/uploads/2017/03/grammargraphics.jpg" alt="Grammar of graphics, CC BYRStudio" width="456" height="342" data-lazy-loaded="true" />

The above is adapted from RStudio’s (terrific) <a href="https://www.rstudio.com/resources/cheatsheets/" target="_blank" rel="nofollow">ggplot2 cheat sheet</a>, which in turn is based principles from Wickham 2010, <a href="http://byrneslab.net/classes/biol607/readings/wickham_layered-grammar.pdf" target="_blank" rel="nofollow">A Layered Grammar of Graphics</a>. (If you haven’t read it, it is <em>well</em> worth the time, even if you’re an experienced ggploter).

This grammar defines what we need to explain how a plot is organized and arranged. When you follow the grammar of graphics, the syntax of the code involves only <em>important decisions</em>– choices that directly impact a user’s interpretation of the data.

<img src="https://i2.wp.com/www.dropbox.com/s/3pf8lc7uwlis4fc/Screenshot%202016-02-12%2010.07.11.png?w=456&amp;ssl=1" alt="what each ggplot line does" width="177" height="40" data-recalc-dims="1" data-lazy-loaded="true" />

Could you imagine a shorter version of this code for making the by-gene plot? (Not by, say, making function names shorter: I mean a version with fewer symbolic tokens). Not particularly.<sup id="fnref:defaults"><a class="footnote" href="http://varianceexplained.org/r/why-I-use-ggplot2/#fn:defaults" target="_blank" rel="nofollow">4</a></sup> This is a compact encoding of the rules for creating this graph from this data. Viewed that way, the base plot code is a decompressed version: it’s an attempt at fulfilling this specification.

The difference comes down to this:
<ul>
 	<li>Base plotting is <strong>imperative</strong>, it’s about what <strong>you <em>do</em></strong>. You set up your <code class="highlighter-rouge">layout()</code>, then you go to the first gene. You add the points for that gene along with a title. Then you fit and plot a best-fit-line for the first nutrient, then the second nutrient, and so on. Then you go on to the next plot. After 20 of those, you end with a legend.</li>
 	<li>ggplot2 plotting is <strong>declarative</strong>, it’s about what <strong>your graph <em>is</em></strong>. The graph has <code class="highlighter-rouge">rate</code> mapped to the x-axis, <code class="highlighter-rouge">expression</code> mapped to the y, and <code class="highlighter-rouge">nutrient</code> mapped to the color. The graph displays both points and best-fit lines for each gene. And it’s faceted into one-plot-per-gene, with a gene described by its systematic ID and common name.</li>
</ul>
Once you have the latter description, the idea of writing loops, if statements, grid statements, and so on is superfluous. It’s not giving you more control over the graph, it’s giving you busywork.
<h3 id="conclusion-challenge-me">Conclusion: Challenge me</h3>
Jeff makes the claim, in this post and elsewhere, that ggplot2 is restrictive: that there is some superset of graphs that cannot be expressed in ggplot2 but can in base plotting. I’m skeptical of this, simply because I’ve been looking for such a graph in several years of professional ggplot2 use and it’s pretty rare to run into one.<sup id="fnref:twoaxes"><a class="footnote" href="http://varianceexplained.org/r/why-I-use-ggplot2/#fn:twoaxes" target="_blank" rel="nofollow">5</a></sup> I have, however, found a rather extraordinary range of things you <em>can</em> express in them. For instance, consider this gganimation:

<img src="http://the-r.kr/wp-content/uploads/2017/03/density.gif" alt="kernel density estimation" width="456" height="456" data-lazy-loaded="true" />

This animation has a lot going on. But it fits naturally into a ggplot2 + <a href="https://github.com/dgrtwo/gganimate" target="_blank" rel="nofollow">gganimate</a> call (<a href="http://varianceexplained.org/files/bandwidth.html" target="_blank" rel="nofollow">check out the code</a>!). Jeff credits ggplot2 for its animation package (thanks Jeff!) but doesn’t consider why it’s so easy to extend ggplot2 with animation (just a <code class="highlighter-rouge">frame = </code>argument), while an equally concise version in base plotting (adding a <code class="highlighter-rouge">frame</code> argument to <code class="highlighter-rouge">plot</code>, <code class="highlighter-rouge">boxplot</code>, <code class="highlighter-rouge">points</code>, etc) would be basically impossible.<sup id="fnref:animation"><a class="footnote" href="http://varianceexplained.org/r/why-I-use-ggplot2/#fn:animation" target="_blank" rel="nofollow">6</a></sup> It’s because once you think of a graph as mapping data to aesthetics, rather than a set of separate tools applied in sequence, adding an additional aesthetic- that of time- is straightforward.

But it’s impossible to prove a negative- I can’t say “you can make some complicated plots, so there’s no plots you can’t make”. So I’ll ask Jeff and others who consider ggplot2 overly restrictive. <strong>What are examples of plots that are more difficult in ggplot2 than in base?</strong>

I’ve already made the concession of clustered heatmaps, and I’m sure there are other types I’m willing to concede. But I suspect a lot of plots are much easier than he thinks. For instance, Jeff links to <a href="http://rafalab.dfci.harvard.edu/images/frontb300.png" target="_blank" rel="nofollow">this plot</a> as one that requires “quite a bit of work” in ggplot2, and I’m not sure why. If he could find the raw data for that plot, I’d be happy to try it.

So what do you say?
<div class="footnotes">
<ol>
 	<li id="fn:heatmap2">For production-ready heatmaps cases I’ll typically use <a href="http://www.inside-r.org/packages/cran/gplots/docs/heatmap.2" target="_blank" rel="nofollow"><code class="highlighter-rouge">heatmap.2</code> from gplots</a> instead, but that is built on base plotting as well. <a class="reversefootnote" href="http://varianceexplained.org/r/why-I-use-ggplot2/#fnref:heatmap2" target="_blank" rel="nofollow">↩</a></li>
 	<li id="fn:matplot">A base R user may bring up the <code class="highlighter-rouge">matplot</code> function, which is sort of a special case for such plots, but that function causes more problems than it solves. Among other issues, its input format, a matrix with one column per group, is inconsistent with almost all other plotting functions in base <em>or</em> ggplot2. And as soon as you want to add (say) a smoothing curve, you’re going to start fiddling with loops and <code class="highlighter-rouge">apply</code>s or just reshaping your data into a tidy form anyway. <a class="reversefootnote" href="http://varianceexplained.org/r/why-I-use-ggplot2/#fnref:matplot" target="_blank" rel="nofollow">↩</a></li>
 	<li id="fn:theme">I am a bit puzzled by Jeff’s accusation that “without [the ggthemes package] for some specific plot, it would require more coding.” Well, yes, that’s why it’s nice that the package exists! <a class="reversefootnote" href="http://varianceexplained.org/r/why-I-use-ggplot2/#fnref:theme" target="_blank" rel="nofollow">↩</a></li>
 	<li id="fn:defaults">You could have replaced the first two lines with <code class="highlighter-rouge">qplot(rate, expression, color = nutrient, data = top_data, geom = "point")</code>, but that encodes exactly the same information while saving just a few characters. One other way it could have been appreciably more compact: if the defaults for <code class="highlighter-rouge">method, </code>se<code class="highlighter-rouge">, and </code>scales<code class="highlighter-rouge"> had been closer to our choices. Of these, I think there's a case to be made that </code>geom_smooth<code class="highlighter-rouge">'s </code>se<code class="highlighter-rouge"> argument should have been false by default. </code>ggplot2` is far from perfect! <a class="reversefootnote" href="http://varianceexplained.org/r/why-I-use-ggplot2/#fnref:defaults" target="_blank" rel="nofollow">↩</a></li>
 	<li id="fn:twoaxes">Except two y axes on the same plot! That is absolutely impossible in ggplot2. <a href="http://stackoverflow.com/a/3101876/712603" target="_blank" rel="nofollow">But I agree with Hadley</a> that they’re a bad idea anyway. <a class="reversefootnote" href="http://varianceexplained.org/r/why-I-use-ggplot2/#fnref:twoaxes" target="_blank" rel="nofollow">↩</a></li>
 	<li id="fn:animation">In fact, the <a href="http://yihui.name/animation/" target="_blank" rel="nofollow">animation package</a> by Yihui Xie works equally well with either base plotting or ggplot2, and gganimate uses the package to create its own animations. But there’s a reason Jeff appreciates gganimate’s approach: you’re getting rid of an extra step of programming loops and logic, just as ggplot2 does with faceting, grouped lines, and so on. <a class="reversefootnote" href="http://varianceexplained.org/r/why-I-use-ggplot2/#fnref:animation" target="_blank" rel="nofollow">↩</a></li>
</ol>
</div>
소스: <em><a href="https://www.r-bloggers.com/why-i-use-ggplot2/">Why I use ggplot2 | R-bloggers</a></em>