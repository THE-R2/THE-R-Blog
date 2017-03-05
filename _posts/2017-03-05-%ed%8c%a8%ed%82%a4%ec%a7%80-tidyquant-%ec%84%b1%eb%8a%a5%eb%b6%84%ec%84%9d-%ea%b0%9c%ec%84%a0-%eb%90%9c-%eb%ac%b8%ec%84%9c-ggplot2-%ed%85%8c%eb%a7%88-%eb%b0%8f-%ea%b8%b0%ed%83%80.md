---
ID: 1546
post_title: '[패키지] tidyquant : 성능분석, 개선 된 문서, ggplot2 테마 및 기타'
author: The-R
post_date: 2017-03-05 10:48:27
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/03/05/%ed%8c%a8%ed%82%a4%ec%a7%80-tidyquant-%ec%84%b1%eb%8a%a5%eb%b6%84%ec%84%9d-%ea%b0%9c%ec%84%a0-%eb%90%9c-%eb%ac%b8%ec%84%9c-ggplot2-%ed%85%8c%eb%a7%88-%eb%b0%8f-%ea%b8%b0%ed%83%80/'
published: true
inline_featured_image:
  - "0"
avada_post_views_count:
  - "2"
scc_share_count_google+:
  - "0"
scc_share_count_facebook:
  - "-1"
scc_share_count_pocket:
  - "0"
scc_share_count_hatebu:
  - "0"
scc_share_count_crawldate:
  - 2017/03/05 10:57:58
scc_share_count_total:
  - "0"
sbg_selected_sidebar:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_replacement:
  - 'a:1:{i:0;s:0:"";}'
sbg_selected_sidebar_2:
  - 'a:1:{i:0;s:1:"0";}'
sbg_selected_sidebar_2_replacement:
  - 'a:1:{i:0;s:0:"";}'
slide_template:
  - default
---
I’m excited to announce the release of <code class="highlighter-rouge">tidyquant</code> version 0.4.0!!! The release is yet again sizable. It includes <strong>integration with the <code class="highlighter-rouge">PerformanceAnalytics</code> package</strong>, which now enables full financial analyses to be performed without ever leaving the “tidyverse” (i.e. <strong>with DATA FRAMES</strong>). The integration includes the ability to perform performance analysis and portfolio attribution at scale (i.e. with many stocks or many portfolios at once)! But wait there’s more… In addition to an introduction vignette, we created <strong>five (yes, five!) topic-specific vignettes</strong> designed to reduce the learning curve for <em>financial data scientists</em>. We also have <strong>new <code class="highlighter-rouge">ggplot2</code> themes</strong> to assist with creating beautiful and meaningful financial charts. We included <code class="highlighter-rouge">tq_get</code> support for <strong>“compound getters”</strong> so multiple data sources can be brought into a nested data frame all at once. Last, we have added new <code class="highlighter-rouge">tq_index()</code> and <code class="highlighter-rouge">tq_exchange()</code> functions to make collecting stock data with <code class="highlighter-rouge">tq_get</code> even easier. I’ll briefly touch on several of the updates. The package is open source, and you can view the code on the <a href="https://github.com/mdancho84/tidyquant" target="_blank" rel="nofollow">tidyquant github page</a>.
<h1 id="table-of-contents">Table of Contents</h1>
<ul>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#prerequisites" target="_blank" rel="nofollow">Prerequisites</a></li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#overview" target="_blank" rel="nofollow">Overview</a></li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#updates" target="_blank" rel="nofollow">v0.4.0 Updates</a>
<ul>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#example1" target="_blank" rel="nofollow">1: PerformanceAnalytics Integration</a></li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#example2" target="_blank" rel="nofollow">2: New User-Friendly Vignettes</a></li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#example3" target="_blank" rel="nofollow">3: New ggplot2 Themes</a></li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#example4" target="_blank" rel="nofollow">4: “Compound Getters” in tq_get</a></li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#example5" target="_blank" rel="nofollow">5: tq_index and tq_exchange</a></li>
</ul>
</li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#conclusion" target="_blank" rel="nofollow">Conclusion</a></li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#recap" target="_blank" rel="nofollow">Recap</a></li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#further-reading" target="_blank" rel="nofollow">Further Reading</a></li>
</ul>
<h1 id="prerequisites-">Prerequisites<a id="prerequisites" class="anchor"></a></h1>
First, update to <code class="highlighter-rouge">tidyquant</code> v0.4.0.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">install.packages</span><span class="p">(</span><span class="s2">"tidyquant"</span><span class="p">)</span></code></pre>
</figure>Next, load <code class="highlighter-rouge">tidyquant</code>.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="c1"># Loads tidyquant, tidyverse, lubridate, quantmod, TTR, xts, zoo, PerformanceAnalytics
</span><span class="n">library</span><span class="p">(</span><span class="n">tidyquant</span><span class="p">)</span></code></pre>
</figure>Load the <code class="highlighter-rouge">FANG</code> data set, which will be used in the examples. The <code class="highlighter-rouge">FANG</code> data set contains the historical stock prices for FB, AMZN, NFLX, and GOOG from the beginning of 2013 through the end of 2016.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">data</span><span class="p">(</span><span class="n">FANG</span><span class="p">)</span>
<span class="n">FANG</span></code></pre>
</figure><figure class="highlight">
<pre><code class="language-text" data-lang="text">## # A tibble: 4,032 × 8
##    symbol       date  open  high   low close    volume adjusted
##     &lt;chr&gt;     &lt;date&gt; &lt;dbl&gt; &lt;dbl&gt; &lt;dbl&gt; &lt;dbl&gt;     &lt;dbl&gt;    &lt;dbl&gt;
## 1      FB 2013-01-02 27.44 28.18 27.42 28.00  69846400    28.00
## 2      FB 2013-01-03 27.88 28.47 27.59 27.77  63140600    27.77
## 3      FB 2013-01-04 28.01 28.93 27.83 28.76  72715400    28.76
## 4      FB 2013-01-07 28.69 29.79 28.65 29.42  83781800    29.42
## 5      FB 2013-01-08 29.51 29.60 28.86 29.06  45871300    29.06
## 6      FB 2013-01-09 29.67 30.60 29.49 30.59 104787700    30.59
## 7      FB 2013-01-10 30.60 31.45 30.28 31.30  95316400    31.30
## 8      FB 2013-01-11 31.28 31.96 31.10 31.72  89598000    31.72
## 9      FB 2013-01-14 32.08 32.21 30.62 30.95  98892800    30.95
## 10     FB 2013-01-15 30.64 31.71 29.88 30.10 173242600    30.10
## # ... with 4,022 more rows</code></pre>
</figure>I also recommend the open-source <a href="https://www.rstudio.com/" target="_blank" rel="nofollow">RStudio</a> IDE, which makes <em>R Programming</em> easy and efficient especially for financial analysis.
<h1 id="overview-">Overview<a id="overview" class="anchor"></a></h1>
<blockquote>tidyquant: Bringing financial analysis to the tidyverse</blockquote>
Before I dive into the updates, if you are new to <code class="highlighter-rouge">tidyquant</code> there’s a few core functions that you need to be aware of:
<ul>
 	<li><strong>Getting Financial Data from the web: <code class="highlighter-rouge">tq_get()</code></strong>. This is a one-stop shop for getting web-based financial data in a “tidy” data frame format. Get data for daily stock prices (historical), key statistics (real-time), key ratios (historical), financial statements, dividends, splits, economic data from the FRED, FOREX rates from Oanda.</li>
 	<li><strong>Manipulating Financial Data: <code class="highlighter-rouge">tq_transmute()</code> and <code class="highlighter-rouge">tq_mutate()</code></strong>. Integration for many financial functions from <code class="highlighter-rouge">xts</code>, <code class="highlighter-rouge">zoo</code>, <code class="highlighter-rouge">quantmod</code> and <code class="highlighter-rouge">TTR</code> packages. <code class="highlighter-rouge">tq_mutate()</code> is used to add a column to the data frame, and <code class="highlighter-rouge">tq_transmute()</code> is used to return a new data frame which is necessary for periodicity changes. <strong>Important:</strong> In v0.4.0, <code class="highlighter-rouge">tq_transmute()</code> replaces <code class="highlighter-rouge">tq_transform()</code> for consistency with <code class="highlighter-rouge">dplyr::transmute()</code>.</li>
 	<li><strong>Coercing Data To and From xts and tibble: <code class="highlighter-rouge">as_tibble()</code>and <code class="highlighter-rouge">as_xts()</code></strong>. There are a ton of <a href="http://stackoverflow.com/search?q=xts+data+frame" target="_blank" rel="nofollow">Stack Overflow articles</a> on converting data frames to and from xts. These two functions can be used to answer 99% of these questions.</li>
 	<li><strong>Performance Analysis and Portfolio Analysis: <code class="highlighter-rouge">tq_performance()</code> and <code class="highlighter-rouge">tq_portfolio()</code></strong>. The newest additions to the <code class="highlighter-rouge">tidyquant</code> family integrate <code class="highlighter-rouge">PerformanceAnalytics</code> functions. <code class="highlighter-rouge">tq_performance()</code> converts investment returns into performance metrics. <code class="highlighter-rouge">tq_portfolio()</code> aggregates a group (or multiple groups) of asset returns into one or more portfolios.</li>
</ul>
To learn more, <a href="https://cran.r-project.org/package=tidyquant" target="_blank" rel="nofollow">browse the new and improved vignettes</a>.
<h1 id="v040-updates-">v0.4.0 Updates<a id="updates" class="anchor"></a></h1>
We’ve got some neat examples to show off the new capabilities:
<ol>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#example1" target="_blank" rel="nofollow">PerformanceAnalytics Integration</a></li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#example2" target="_blank" rel="nofollow">New User-Friendly Vignettes</a></li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#example3" target="_blank" rel="nofollow">New ggplot2 Themes</a></li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#example4" target="_blank" rel="nofollow">“Compound Getters” in tq_get</a></li>
 	<li><a href="http://www.business-science.io/code-tools/2017/03/04/tidyquant-update-0-4-0.html#example5" target="_blank" rel="nofollow">tq_index and tq_exchange</a></li>
</ol>
<h2 id="1-performanceanalytics-integration-">1: PerformanceAnalytics Integration<a id="example1" class="anchor"></a></h2>
The <code class="highlighter-rouge">PerformanceAnalytics</code> package does two things very well. First, it enables performance analysis of investment returns using a wide variety of metrics that are detailed in the text, <a href="https://www.amazon.com/Practical-Portfolio-Performance-Measurement-Attribution/dp/0470059281" target="_blank" rel="nofollow"><em>“Practical Portfolio Performance Measurement and Attribution”</em> by Carl Bacon</a>. Second, it enables portfolio aggregation, the process of aggregating a weighted group of stocks or investments into a single set of returns. When combined, this functionality enables <a href="https://en.wikipedia.org/wiki/Performance_attribution" target="_blank" rel="nofollow">portfolio attribution</a>, a set of techniques used to explain a portfolio’s performance versus a benchmark.

The next few examples show off some of the basic capability. These examples scratch the surface of the full capability. Below is a figure demonstrating multiple portfolio analysis, which is an advanced topic discussed in the vignette.

<img src="http://the-r.kr/wp-content/uploads/2017/03/tidyquant-040.png" alt="Portfolio Analysis" width="456" height="269" data-lazy-loaded="true" />
<h3 id="a-stock-performance-analysis">A: Stock Performance Analysis</h3>
The <strong>Sharpe ratio</strong> is commonly used in finance as a measure of return per unit risk. The larger the value, the better the reward-to-risk trade off. The <code class="highlighter-rouge">PerformanceAnalytics</code> package contains a function <code class="highlighter-rouge">SharpeRatio</code> (and <code class="highlighter-rouge">SharpeRatio.modified</code>) that can be used to quickly calculate from a set of returns. We’ll use <code class="highlighter-rouge">tq_performance</code> to calculate the Sharpe ratio in a “tidy” way, using the <code class="highlighter-rouge">PerformanceAnalytics</code> integration. Call <code class="highlighter-rouge">tq_performance_fun_options()</code> to see a full list of integrated functions. <em>Spoiler alert: there’s 128 functions divided into 14 categories.</em>

<code class="highlighter-rouge">tq_performance()</code> allows us to apply <code class="highlighter-rouge">SharpeRatio</code> to “tidy” data frames. The <code class="highlighter-rouge">tq_performance()</code> function uses <code class="highlighter-rouge">Ra</code> and <code class="highlighter-rouge">Rb</code> to specify the asset returns and baseline returns, respectively. These values get passed to the <code class="highlighter-rouge">performance_fun</code>, which in our case will be <code class="highlighter-rouge">SharpeRatio</code>. The <code class="highlighter-rouge">...</code> allows the user to pass additional arguments to the underlying <code class="highlighter-rouge">PerformanceAnalytics</code> function. The arguments are shown below.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">args</span><span class="p">(</span><span class="n">tq_performance</span><span class="p">)</span></code></pre>
</figure><figure class="highlight">
<pre><code class="language-text" data-lang="text">## function (data, Ra, Rb = NULL, performance_fun, ...) 
## NULL</code></pre>
</figure>To understand the end goal, we need to analyze the <code class="highlighter-rouge">SharpeRatio</code> function. The arguments are displayed below. It contains <code class="highlighter-rouge">R</code> a set of returns, <code class="highlighter-rouge">Rf</code> the risk-free rate, <code class="highlighter-rouge">p</code> the confidence level, and <code class="highlighter-rouge">FUN</code> the value of the denominator (default returns Sharpe ratio using all three), and a few other functions that are not used in this example. It’s important to recognize that <code class="highlighter-rouge">R</code> in the <code class="highlighter-rouge">SharpeRatio()</code> function is specified using asset returns (<code class="highlighter-rouge">Ra</code>) in the <code class="highlighter-rouge">tq_performance()</code> function. The baseline returns argument (<code class="highlighter-rouge">Rb</code>) in the <code class="highlighter-rouge">tq_performance()</code> function is not required since the baseline is not required to calculate <code class="highlighter-rouge">SharpeRatio</code>. Just keep in mind that you will either see <code class="highlighter-rouge">R</code> or the combination of <code class="highlighter-rouge">Ra, Rb</code> in the <code class="highlighter-rouge">PerformanceAnalytics</code> function arguments, which indicates whether or not <code class="highlighter-rouge">Rb</code> is required in <code class="highlighter-rouge">tq_performance()</code>.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">args</span><span class="p">(</span><span class="n">SharpeRatio</span><span class="p">)</span></code></pre>
</figure><figure class="highlight">
<pre><code class="language-text" data-lang="text">## function (R, Rf = 0, p = 0.95, FUN = c("StdDev", "VaR", "ES"), 
##     weights = NULL, annualize = FALSE, ...) 
## NULL</code></pre>
</figure>Now that we understand the function, we can easily begin the task of getting the Sharpe ratios for the “FANG” stocks. It involves three steps:
<ol>
 	<li>Get data with <code class="highlighter-rouge">tq_get</code> (already done since we have <code class="highlighter-rouge">FANG</code> loaded). Make sure to group by symbol if the tibble includes prices for multiple stocks.</li>
 	<li>Transmute to period returns with <code class="highlighter-rouge">tq_transmute(mutate_fun = periodReturn)</code></li>
 	<li>Calculate Sharpe ratio with <code class="highlighter-rouge">tq_performance(performance_fun = SharpeRatio)</code></li>
</ol>
<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">FANG</span> <span class="o">%&gt;%</span>
    <span class="n">group_by</span><span class="p">(</span><span class="n">symbol</span><span class="p">)</span> <span class="o">%&gt;%</span>
    <span class="n">tq_transmute</span><span class="p">(</span><span class="n">ohlc_fun</span>   <span class="o">=</span> <span class="n">Ad</span><span class="p">,</span>
                 <span class="n">mutate_fun</span> <span class="o">=</span> <span class="n">periodReturn</span><span class="p">,</span>
                 <span class="n">period</span>     <span class="o">=</span> <span class="s2">"daily"</span><span class="p">)</span> <span class="o">%&gt;%</span>
    <span class="n">tq_performance</span><span class="p">(</span><span class="n">Ra</span>              <span class="o">=</span> <span class="n">daily.returns</span><span class="p">,</span>
                   <span class="n">Rb</span>              <span class="o">=</span> <span class="kc">NULL</span><span class="p">,</span>
                   <span class="n">performance_fun</span> <span class="o">=</span> <span class="n">SharpeRatio</span><span class="p">,</span>
                   <span class="n">Rf</span>              <span class="o">=</span> <span class="m">0</span><span class="p">,</span>
                   <span class="n">p</span>               <span class="o">=</span> <span class="m">0.95</span><span class="p">,</span>
                   <span class="n">FUN</span>             <span class="o">=</span> <span class="s2">"StdDev"</span><span class="p">)</span></code></pre>
</figure><figure class="highlight">
<pre><code class="language-text" data-lang="text">## Source: local data frame [4 x 2]
## Groups: symbol [4]
## 
##   symbol `StdDevSharpe(Rf=0%,p=95%)`
##    &lt;chr&gt;                       &lt;dbl&gt;
## 1     FB                  0.07439327
## 2   AMZN                  0.06442433
## 3   NFLX                  0.08402702
## 4   GOOG                  0.05825002</code></pre>
</figure>It’s very easy to get performance metrics for multiple stocks. Next, we’ll take a look at portfolio performance.
<h3 id="b-basic-portfolio-performance">B: Basic Portfolio Performance</h3>
Combining a group of assets into a portfolio is one of the most useful techniques for controlling risk versus reward. The blending of assets naturally diversifies and can reduce downside risk. Further, portfolio attribution is a set of techniques used to analyze a portfolio or set of portfolios against a benchmark. The newest vignette, <a href="https://cran.r-project.org/package=tidyquant" target="_blank" rel="nofollow">Performance Analysis with tidyquant</a>, breaks the process into several steps shown in the workflow diagram below.

<img src="http://the-r.kr/wp-content/uploads/2017/03/performance_analysis_workflow.png" alt="Portfolio Workflow" width="456" height="411" data-lazy-loaded="true" />

The process for a single portfolio aggregation without a benchmark is shown below. Portfolio aggregation requires a set of weights that can be applied to the various assets (stocks) in the portfolio. Our portfolio consists of FB, AMZN, NFLX, and GOOG. Passing the weights of 50%, 25%, 25%, and 0% blends and aggregates into one set of portfolio returns.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">weights</span> <span class="o">&lt;-</span> <span class="nf">c</span><span class="p">(</span><span class="m">0.50</span><span class="p">,</span> <span class="m">0.25</span><span class="p">,</span> <span class="m">0.25</span><span class="p">,</span> <span class="m">0.00</span><span class="p">)</span>
<span class="n">FANG_portfolio</span> <span class="o">&lt;-</span> <span class="n">FANG</span> <span class="o">%&gt;%</span> 
    <span class="n">group_by</span><span class="p">(</span><span class="n">symbol</span><span class="p">)</span> <span class="o">%&gt;%</span>
    <span class="n">tq_transmute</span><span class="p">(</span><span class="n">ohlc_fun</span>   <span class="o">=</span> <span class="n">Ad</span><span class="p">,</span>
                 <span class="n">mutate_fun</span> <span class="o">=</span> <span class="n">periodReturn</span><span class="p">,</span>
                 <span class="n">period</span>     <span class="o">=</span> <span class="s2">"monthly"</span><span class="p">)</span> <span class="o">%&gt;%</span>
    <span class="n">tq_portfolio</span><span class="p">(</span><span class="n">assets_col</span>  <span class="o">=</span> <span class="n">symbol</span><span class="p">,</span>
                 <span class="n">returns_col</span> <span class="o">=</span> <span class="n">monthly.returns</span><span class="p">,</span>
                 <span class="n">weights</span>     <span class="o">=</span> <span class="n">weights</span><span class="p">)</span>
<span class="n">FANG_portfolio</span></code></pre>
</figure><figure class="highlight">
<pre><code class="language-text" data-lang="text">## # A tibble: 48 × 2
##          date portfolio.returns
##        &lt;date&gt;             &lt;dbl&gt;
## 1  2013-01-31       0.260144557
## 2  2013-02-28      -0.004558003
## 3  2013-03-28      -0.019454685
## 4  2013-04-30       0.080958243
## 5  2013-05-31      -0.013883075
## 6  2013-06-28      -0.017906983
## 7  2013-07-31       0.253520291
## 8  2013-08-30       0.103866369
## 9  2013-09-30       0.145446247
## 10 2013-10-31       0.041956895
## # ... with 38 more rows</code></pre>
</figure>At this point, it’s nice to visualize using a wealth index, which shows the growth of the portfolio. The wealth index is actually an option in <code class="highlighter-rouge">tq_portfolio</code>, but it can also be created by converting the portfolio returns using the <code class="highlighter-rouge">cumprod()</code> function shown below.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">init.investment</span> <span class="o">&lt;-</span> <span class="m">10000</span>
<span class="n">FANG_portfolio</span> <span class="o">%&gt;%</span>
    <span class="n">mutate</span><span class="p">(</span><span class="n">wealth.index</span> <span class="o">=</span> <span class="n">init.investment</span> <span class="o">*</span> <span class="nf">cumprod</span><span class="p">(</span><span class="m">1</span> <span class="o">+</span> <span class="n">portfolio.returns</span><span class="p">))</span> <span class="o">%&gt;%</span>
    <span class="n">ggplot</span><span class="p">(</span><span class="n">aes</span><span class="p">(</span><span class="n">x</span> <span class="o">=</span> <span class="n">date</span><span class="p">,</span> <span class="n">y</span> <span class="o">=</span> <span class="n">wealth.index</span><span class="p">))</span> <span class="o">+</span>
    <span class="n">geom_line</span><span class="p">(</span><span class="n">size</span> <span class="o">=</span> <span class="m">2</span><span class="p">,</span> <span class="n">color</span> <span class="o">=</span> <span class="n">palette_light</span><span class="p">()[[</span><span class="m">3</span><span class="p">]])</span> <span class="o">+</span>
    <span class="n">geom_smooth</span><span class="p">(</span><span class="n">method</span> <span class="o">=</span> <span class="s2">"loess"</span><span class="p">)</span> <span class="o">+</span>
    <span class="n">labs</span><span class="p">(</span><span class="n">title</span> <span class="o">=</span> <span class="s2">"Individual Portfolio: Comparing the Growth of $10K"</span><span class="p">,</span>
         <span class="n">subtitle</span> <span class="o">=</span> <span class="s2">"Quickly visualize performance"</span><span class="p">,</span>
         <span class="n">x</span> <span class="o">=</span> <span class="s2">""</span><span class="p">,</span> <span class="n">y</span> <span class="o">=</span> <span class="s2">"Investment Value"</span><span class="p">)</span> <span class="o">+</span>
    <span class="n">theme_tq</span><span class="p">()</span> <span class="o">+</span>
    <span class="n">scale_y_continuous</span><span class="p">(</span><span class="n">labels</span> <span class="o">=</span> <span class="n">scales</span><span class="o">::</span><span class="n">dollar</span><span class="p">)</span></code></pre>
</figure><img src="http://the-r.kr/wp-content/uploads/2017/03/unnamed-chunk-8-1.png" alt="plot of chunk unnamed-chunk-8" width="456" height="326" data-lazy-loaded="true" />

We can even get some performance metrics using <code class="highlighter-rouge">PerformanceAnalytics</code> functions. The table functions are the most useful since they calculate groups of portfolio attribution metrics. <strong>Eighteen different table functions are available</strong>. We’ll use the <code class="highlighter-rouge">table.Stats</code> function, which returns a “tidy” set of 15 summary statistics on the stock returns including arithmetic mean, standard deviation, skewness, kurtosis, and more.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">FANG_portfolio</span> <span class="o">%&gt;%</span>
    <span class="n">tq_performance</span><span class="p">(</span><span class="n">Ra</span> <span class="o">=</span> <span class="n">portfolio.returns</span><span class="p">,</span>
                   <span class="n">Rb</span> <span class="o">=</span> <span class="kc">NULL</span><span class="p">,</span>
                   <span class="n">performance_fun</span> <span class="o">=</span> <span class="n">table.Stats</span><span class="p">)</span></code></pre>
</figure><figure class="highlight">
<pre><code class="language-text" data-lang="text">## # A tibble: 1 × 16
##   ArithmeticMean GeometricMean Kurtosis `LCLMean(0.95)` Maximum
## *          &lt;dbl&gt;         &lt;dbl&gt;    &lt;dbl&gt;           &lt;dbl&gt;   &lt;dbl&gt;
## 1         0.0379        0.0347   0.5327          0.0138  0.2601
## # ... with 11 more variables: Median &lt;dbl&gt;, Minimum &lt;dbl&gt;, NAs &lt;dbl&gt;,
## #   Observations &lt;dbl&gt;, Quartile1 &lt;dbl&gt;, Quartile3 &lt;dbl&gt;,
## #   SEMean &lt;dbl&gt;, Skewness &lt;dbl&gt;, Stdev &lt;dbl&gt;, `UCLMean(0.95)` &lt;dbl&gt;,
## #   Variance &lt;dbl&gt;</code></pre>
</figure>There’s also capability for <strong>performance attribution</strong> (comparing portfolio performance against a benchmark) and <strong>scaling analyses to multiple portfolios</strong>. For those interested in furthering the analysis, please visit the new vignette, <a href="https://cran.r-project.org/package=tidyquant" target="_blank" rel="nofollow">Performance Analysis with tidyquant</a>.
<h2 id="2-new-user-friendly-vignettes-">2: New User-Friendly Vignettes<a id="example2" class="anchor"></a></h2>
Financial analysis can be overwhelming due to the depth and breadth of various topics. Add to it a new package with new functions and workflows, and the task can seem impossible. The good news is <strong>we understand</strong>.

We are actively taking steps to reduce the learning curve so you can get up to speed quickly. While the work is not done yet, we believe that the vignettes are a good place to start. The goal is to break down complex tasks without overloading the user with everything at once. There is now one main “introduction” that links to five topic-specific vignettes. Each topical vignette covers the basics behind the package including real-world examples so you can see how the package can be implemented. You can access the <a href="https://cran.r-project.org/package=tidyquant" target="_blank" rel="nofollow">new vignettes here</a>.

<img src="http://the-r.kr/wp-content/uploads/2017/03/tidyquant-vignettes.png" alt="tidyquant vignettes" width="456" height="327" data-lazy-loaded="true" />
<h2 id="3-new-ggplot2-themes-">3: New ggplot2 Themes<a id="example3" class="anchor"></a></h2>
<code class="highlighter-rouge">tidyquant</code> ships with some new themes to assist with creating beautiful and meaningful financial charts: <code class="highlighter-rouge">theme_tq()</code> and some extra fun ones including <code class="highlighter-rouge">theme_tq_dark()</code> and <code class="highlighter-rouge">theme_tq_green()</code>. To coordinate aesthetic colors and fills with the appropriate theme, we’ve added <code class="highlighter-rouge">scale_color_tq(theme = "light")</code>. You can modify the <code class="highlighter-rouge">theme</code> arg to get the colors to correspond with the different themes. In addition, we have <code class="highlighter-rouge">palette_light()</code>, <code class="highlighter-rouge">palette_dark()</code> and <code class="highlighter-rouge">palette_green()</code> for those interested in using the color palette. Here’s a quick example.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">FANG</span> <span class="o">%&gt;%</span>
    <span class="n">group_by</span><span class="p">(</span><span class="n">symbol</span><span class="p">)</span> <span class="o">%&gt;%</span>
    <span class="n">tq_transmute</span><span class="p">(</span><span class="n">ohlc_fun</span>   <span class="o">=</span> <span class="n">Ad</span><span class="p">,</span>
                 <span class="n">mutate_fun</span> <span class="o">=</span> <span class="n">periodReturn</span><span class="p">,</span>
                 <span class="n">period</span>     <span class="o">=</span> <span class="s2">"monthly"</span><span class="p">)</span> <span class="o">%&gt;%</span>
    <span class="n">mutate</span><span class="p">(</span><span class="n">wealth.index</span> <span class="o">=</span> <span class="m">10000</span> <span class="o">*</span> <span class="nf">cumprod</span><span class="p">(</span><span class="m">1</span> <span class="o">+</span> <span class="n">monthly.returns</span><span class="p">))</span> <span class="o">%&gt;%</span>
    <span class="n">ggplot</span><span class="p">(</span><span class="n">aes</span><span class="p">(</span><span class="n">x</span> <span class="o">=</span> <span class="n">date</span><span class="p">,</span> <span class="n">y</span> <span class="o">=</span> <span class="n">wealth.index</span><span class="p">,</span> <span class="n">color</span> <span class="o">=</span> <span class="n">symbol</span><span class="p">))</span> <span class="o">+</span>
    <span class="n">geom_line</span><span class="p">(</span><span class="n">size</span> <span class="o">=</span> <span class="m">1.5</span><span class="p">)</span> <span class="o">+</span>
    <span class="n">labs</span><span class="p">(</span><span class="n">title</span> <span class="o">=</span> <span class="s2">"Stocks: Comparing the Growth of $10K"</span><span class="p">,</span>
         <span class="n">subtitle</span> <span class="o">=</span> <span class="s2">"New theme for financial visualizations"</span><span class="p">,</span>
         <span class="n">x</span> <span class="o">=</span> <span class="s2">""</span><span class="p">,</span> <span class="n">y</span> <span class="o">=</span> <span class="s2">"Investment Value"</span><span class="p">)</span> <span class="o">+</span>
    <span class="n">scale_y_continuous</span><span class="p">(</span><span class="n">labels</span> <span class="o">=</span> <span class="n">scales</span><span class="o">::</span><span class="n">dollar</span><span class="p">)</span> <span class="o">+</span>
    <span class="n">theme_tq</span><span class="p">()</span> <span class="o">+</span>
    <span class="n">scale_color_tq</span><span class="p">(</span><span class="n">theme</span> <span class="o">=</span> <span class="s2">"light"</span><span class="p">)</span></code></pre>
</figure><img src="http://the-r.kr/wp-content/uploads/2017/03/unnamed-chunk-10-1.png" alt="plot of chunk unnamed-chunk-10" width="456" height="326" data-lazy-loaded="true" />

For those interested in learning more about the <code class="highlighter-rouge">tidyquant</code> charting capabilities, please visit the updated vignette, <a href="https://cran.r-project.org/package=tidyquant" target="_blank" rel="nofollow">Charting with tidyquant</a>.
<h2 id="4-compound-getters-in-tq_get-">4: “Compound Getters” in tq_get<a id="example4" class="anchor"></a></h2>
Compound getters are a nice tool for those looking to get multiple data sets for one stock symbol. For example, one may want the “key.ratios” and the “key.stats”, which provides key fundamental and financial ratio data on both a historical and real-time basis, respectively. You can now pull this information in one call to <code class="highlighter-rouge">tq_get</code> using a “compound getter”.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">AAPL_data</span> <span class="o">&lt;-</span> <span class="n">tq_get</span><span class="p">(</span><span class="s2">"AAPL"</span><span class="p">,</span> <span class="n">get</span> <span class="o">=</span> <span class="nf">c</span><span class="p">(</span><span class="s2">"key.ratios"</span><span class="p">,</span> <span class="s2">"key.stats"</span><span class="p">))</span>
<span class="n">AAPL_data</span></code></pre>
</figure><figure class="highlight">
<pre><code class="language-text" data-lang="text">## # A tibble: 1 × 3
##   symbol       key.ratios         key.stats
##    &lt;chr&gt;           &lt;list&gt;            &lt;list&gt;
## 1   AAPL &lt;tibble [7 × 2]&gt; &lt;tibble [1 × 55]&gt;</code></pre>
</figure>Let’s examine what’s in the “key.ratios” column using <code class="highlighter-rouge">unnest()</code>.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">AAPL_data</span> <span class="o">%&gt;%</span> <span class="n">unnest</span><span class="p">(</span><span class="n">key.ratios</span><span class="p">)</span> </code></pre>
</figure><figure class="highlight">
<pre><code class="language-text" data-lang="text">## # A tibble: 7 × 3
##   symbol           section               data
##    &lt;chr&gt;             &lt;chr&gt;             &lt;list&gt;
## 1   AAPL        Financials &lt;tibble [150 × 5]&gt;
## 2   AAPL     Profitability &lt;tibble [170 × 5]&gt;
## 3   AAPL            Growth &lt;tibble [160 × 5]&gt;
## 4   AAPL         Cash Flow  &lt;tibble [50 × 5]&gt;
## 5   AAPL  Financial Health &lt;tibble [240 × 5]&gt;
## 6   AAPL Efficiency Ratios  &lt;tibble [80 × 5]&gt;
## 7   AAPL  Valuation Ratios  &lt;tibble [40 × 5]&gt;</code></pre>
</figure>Like peeling away layers we can see whats inside. Let’s do one more <code class="highlighter-rouge">unnest</code>.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">AAPL_data</span> <span class="o">%&gt;%</span> 
    <span class="n">unnest</span><span class="p">(</span><span class="n">key.ratios</span><span class="p">)</span> <span class="o">%&gt;%</span> 
    <span class="n">unnest</span><span class="p">(</span><span class="n">data</span><span class="p">)</span></code></pre>
</figure><figure class="highlight">
<pre><code class="language-text" data-lang="text">## # A tibble: 890 × 7
##    symbol    section sub.section group        category       date
##     &lt;chr&gt;      &lt;chr&gt;       &lt;chr&gt; &lt;dbl&gt;           &lt;chr&gt;     &lt;date&gt;
## 1    AAPL Financials  Financials     1 Revenue USD Mil 2007-09-01
## 2    AAPL Financials  Financials     1 Revenue USD Mil 2008-09-01
## 3    AAPL Financials  Financials     1 Revenue USD Mil 2009-09-01
## 4    AAPL Financials  Financials     1 Revenue USD Mil 2010-09-01
## 5    AAPL Financials  Financials     1 Revenue USD Mil 2011-09-01
## 6    AAPL Financials  Financials     1 Revenue USD Mil 2012-09-01
## 7    AAPL Financials  Financials     1 Revenue USD Mil 2013-09-01
## 8    AAPL Financials  Financials     1 Revenue USD Mil 2014-09-01
## 9    AAPL Financials  Financials     1 Revenue USD Mil 2015-09-01
## 10   AAPL Financials  Financials     1 Revenue USD Mil 2016-09-01
## # ... with 880 more rows, and 1 more variables: value &lt;dbl&gt;</code></pre>
</figure>We can do the same thing with the “key.stats”. Set <code class="highlighter-rouge">.drop = TRUE</code> to remove the “key.ratios” column.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">AAPL_data</span> <span class="o">%&gt;%</span> <span class="n">unnest</span><span class="p">(</span><span class="n">key.stats</span><span class="p">,</span> <span class="n">.drop</span> <span class="o">=</span> <span class="kc">TRUE</span><span class="p">)</span></code></pre>
</figure><figure class="highlight">
<pre><code class="language-text" data-lang="text">## # A tibble: 1 × 56
##   symbol    Ask Ask.Size Average.Daily.Volume    Bid Bid.Size
##    &lt;chr&gt;  &lt;dbl&gt;    &lt;dbl&gt;                &lt;dbl&gt;  &lt;dbl&gt;    &lt;dbl&gt;
## 1   AAPL 139.68      200             28964000 139.53      500
## # ... with 50 more variables: Book.Value &lt;dbl&gt;, Change &lt;dbl&gt;,
## #   Change.From.200.day.Moving.Average &lt;dbl&gt;,
## #   Change.From.50.day.Moving.Average &lt;dbl&gt;,
## #   Change.From.52.week.High &lt;dbl&gt;, Change.From.52.week.Low &lt;dbl&gt;,
## #   Change.in.Percent &lt;dbl&gt;, Currency &lt;chr&gt;, Days.High &lt;dbl&gt;,
## #   Days.Low &lt;dbl&gt;, Days.Range &lt;chr&gt;, Dividend.Pay.Date &lt;date&gt;,
## #   Dividend.per.Share &lt;dbl&gt;, Dividend.Yield &lt;dbl&gt;, EBITDA &lt;dbl&gt;,
## #   EPS &lt;dbl&gt;, EPS.Estimate.Current.Year &lt;dbl&gt;,
## #   EPS.Estimate.Next.Quarter &lt;dbl&gt;, EPS.Estimate.Next.Year &lt;dbl&gt;,
## #   Ex.Dividend.Date &lt;date&gt;, Float.Shares &lt;dbl&gt;, High.52.week &lt;dbl&gt;,
## #   Last.Trade.Date &lt;date&gt;, Last.Trade.Price.Only &lt;dbl&gt;,
## #   Last.Trade.Size &lt;dbl&gt;, Last.Trade.With.Time &lt;chr&gt;,
## #   Low.52.week &lt;dbl&gt;, Market.Capitalization &lt;dbl&gt;,
## #   Moving.Average.200.day &lt;dbl&gt;, Moving.Average.50.day &lt;dbl&gt;,
## #   Name &lt;chr&gt;, Open &lt;dbl&gt;, PE.Ratio &lt;dbl&gt;, PEG.Ratio &lt;dbl&gt;,
## #   Percent.Change.From.200.day.Moving.Average &lt;dbl&gt;,
## #   Percent.Change.From.50.day.Moving.Average &lt;dbl&gt;,
## #   Percent.Change.From.52.week.High &lt;dbl&gt;,
## #   Percent.Change.From.52.week.Low &lt;dbl&gt;, Previous.Close &lt;dbl&gt;,
## #   Price.to.Book &lt;dbl&gt;, Price.to.EPS.Estimate.Current.Year &lt;dbl&gt;,
## #   Price.to.EPS.Estimate.Next.Year &lt;dbl&gt;, Price.to.Sales &lt;dbl&gt;,
## #   Range.52.week &lt;chr&gt;, Revenue &lt;dbl&gt;, Shares.Outstanding &lt;dbl&gt;,
## #   Short.Ratio &lt;dbl&gt;, Stock.Exchange &lt;chr&gt;,
## #   Target.Price.1.yr. &lt;dbl&gt;, Volume &lt;dbl&gt;</code></pre>
</figure>The benefit to “compound getters” is that <strong>all your data is stored in one data frame</strong>. To access it, you can simply <code class="highlighter-rouge">unnest</code> the list columns. Additionally, the “compound getters” can be <strong>scaled</strong> in the same way that a single get can be scaled: with a vector of stock symbols or a data frame of stock symbols with the symbols in the first column. See the next section for scaling using the new <code class="highlighter-rouge">tq_index()</code> and <code class="highlighter-rouge">tq_exchange()</code> functions.
<h2 id="5-tq_index-and-tq_exchange-">5. tq_index and tq_exchange<a id="example5" class="anchor"></a></h2>
We got some really good feedback from a certain someone at <em>RStudio</em> on combining two calls to <code class="highlighter-rouge">tq_get()</code> in a row for retrieving an index of stock symbols (e.g. “SP500”) and then the scaling the retrieval of data for the stock symbols. The advice was really good because (1) it was ugly having two calls to <code class="highlighter-rouge">tq_get()</code> in a row and (2) more importantly it got us thinking how we can improve scaling data collection. Here’s the significant change from “old way” to the “new way”.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="c1"># Not evaluated due to excessive run time
# Old method
</span><span class="n">tq_get</span><span class="p">(</span><span class="s2">"SP500"</span><span class="p">,</span> <span class="n">get</span> <span class="o">=</span> <span class="s2">"stock.index"</span><span class="p">)</span> <span class="o">%&gt;%</span>
    <span class="n">tq_get</span><span class="p">(</span><span class="n">get</span> <span class="o">=</span> <span class="s2">"stock.prices"</span><span class="p">)</span>

<span class="c1"># New method
</span><span class="n">tq_index</span><span class="p">(</span><span class="s2">"SP500"</span><span class="p">)</span> <span class="o">%&gt;%</span>
    <span class="n">tq_get</span><span class="p">(</span><span class="n">get</span> <span class="o">=</span> <span class="s2">"stock.prices"</span><span class="p">)</span></code></pre>
</figure>The separation of a stock list from a call to retrieve the data for each of the stocks is fundamentally a good idea because now we can have more lists. For example, if you want to download stock prices for every stock covered on the NASDAQ exchange, you can use the new <code class="highlighter-rouge">tq_exchange("NASDAQ")</code> to retrieve the stock list and then pipe (<code class="highlighter-rouge">%&gt;%</code>) the list to <code class="highlighter-rouge">tq_get</code>.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">tq_exchange</span><span class="p">(</span><span class="s2">"NASDAQ"</span><span class="p">)</span></code></pre>
</figure><figure class="highlight">
<pre><code class="language-text" data-lang="text">## # A tibble: 3,169 × 7
##    symbol                                company last.sale.price
##     &lt;chr&gt;                                  &lt;chr&gt;           &lt;dbl&gt;
## 1     PIH 1347 Property Insurance Holdings, Inc.            7.20
## 2    FLWS                1-800 FLOWERS.COM, Inc.            9.85
## 3    FCCY          1st Constitution Bancorp (NJ)           18.65
## 4    SRCE                 1st Source Corporation           47.08
## 5    VNET                   21Vianet Group, Inc.            7.10
## 6    TWOU                               2U, Inc.           37.65
## 7    JOBS                            51job, Inc.           35.60
## 8    CAFD             8point3 Energy Partners LP           12.91
## 9    EGHT                                8x8 Inc           14.90
## 10   AVHI                        A V Homes, Inc.           16.85
## # ... with 3,159 more rows, and 4 more variables: market.cap &lt;chr&gt;,
## #   ipo.year &lt;dbl&gt;, sector &lt;chr&gt;, industry &lt;chr&gt;</code></pre>
</figure>Piping to <code class="highlighter-rouge">tq_get</code>. (Warning: <em>A word of caution that this could take 10-20 minutes to download the stock prices for all 3169 stock symbols.</em>)

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="c1"># Not evaluated due to excessive time
</span><span class="n">tq_exchange</span><span class="p">(</span><span class="s2">"NASDAQ"</span><span class="p">)</span> <span class="o">%&gt;%</span>
    <span class="n">tq_get</span><span class="p">(</span><span class="n">get</span> <span class="o">=</span> <span class="s2">"stock.prices"</span><span class="p">)</span></code></pre>
</figure>The combination of <code class="highlighter-rouge">tq_index</code> and <code class="highlighter-rouge">tq_exchange</code> now gives the user access to a wide range of stock lists. To get the full list of options, use <code class="highlighter-rouge">tq_index_options()</code> and <code class="highlighter-rouge">tq_exchange_options()</code>, respectively.
<h1 id="conclusions-">Conclusions<a id="conclusion" class="anchor"></a></h1>
This is an exciting release for a few reasons. First, the <code class="highlighter-rouge">PerformanceAnalytics</code> integration fills a big gap that now allows full financial analysis to be performed within the “tidyverse” (i.e. using data frames only). You can start a workflow with a symbol or set of symbols and through piping (<code class="highlighter-rouge">%&gt;%</code>) to <code class="highlighter-rouge">tq_get</code>, <code class="highlighter-rouge">tq_transmute</code>, and <code class="highlighter-rouge">tq_performance</code> can end with performance metrics all in a few lines of code. Previously this was impossible.

Second, portfolio attribution and performance analysis is now possible in the “tidyverse”. This is very interesting because with the data science workflow discussed in <a href="http://r4ds.had.co.nz/" target="_blank" rel="nofollow">R for Data Science</a> the scale at which portfolios can be modeled and analyzed is limitless (refer to many models and the <code class="highlighter-rouge">purrr</code> package).

Third, data science is a rapidly evolving field with new people joining the community by the second. With this influx we recognize it’s important to reduce the learning curve for “financial data scientists”, those looking to apply data science to finance. As a result, we are actively taking steps to reduce the learning curve. The first step of providing a set of improved vignettes is complete. We will continue to focus on this area in the future.
<h1 id="recap-">Recap<a id="recap" class="anchor"></a></h1>
This post was meant to give users and potential users a flavor for the new additions to <code class="highlighter-rouge">tidyquant</code> v0.4.0. We took a peek at the new <code class="highlighter-rouge">PerformanceAnalytics</code> integration, which enables performance analysis and portfolio aggregation. We introduced the new vignettes, which are topical and are designed to get users up to speed quickly. We discussed several other important new features such as new <code class="highlighter-rouge">ggplot2</code> themes, the new support for “compound getters” in <code class="highlighter-rouge">tq_get</code>, and the new <code class="highlighter-rouge">tq_index</code> and <code class="highlighter-rouge">tq_exchange</code> functions for retrieving stock lists. There are a number of other changes not specifically addressed. Those interested can view the <a href="https://github.com/mdancho84/tidyquant/blob/master/NEWS.md" target="_blank" rel="nofollow">NEWS here</a>.
<h1 id="further-reading-">Further Reading<a id="further-reading" class="anchor"></a></h1>
<ol>
 	<li><strong><a href="https://cran.r-project.org/package=tidyquant" target="_blank" rel="nofollow">Tidyquant Vignettes</a></strong>: This overview just scratches the surface of <code class="highlighter-rouge">tidyquant</code>. The vignettes explain much, much more!</li>
 	<li><strong><a href="http://r4ds.had.co.nz/" target="_blank" rel="nofollow">R for Data Science</a></strong>: A free book that thoroughly covers the “tidyverse”. A prerequisite for maximizing your abilities with <code class="highlighter-rouge">tidyquant</code>.</li>
</ol>
소스: <em><a href="https://www.r-bloggers.com/tidyquant-0-4-0-performanceanalytics-improved-documentation-ggplot2-themes-and-more/">tidyquant 0.4.0: PerformanceAnalytics, Improved Documentation, ggplot2 Themes and More | R-bloggers | R-bloggers</a></em>