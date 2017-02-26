---
ID: 1494
post_title: >
  관계형 데이터의 그래픽
  문법 ggraph 패키지
author: The-R
post_date: 2017-02-26 15:27:57
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/02/26/%ea%b4%80%ea%b3%84%ed%98%95-%eb%8d%b0%ec%9d%b4%ed%84%b0%ec%9d%98-%ea%b7%b8%eb%9e%98%ed%94%bd-%eb%ac%b8%eb%b2%95-ggraph-%ed%8c%a8%ed%82%a4%ec%a7%80/'
published: true
inline_featured_image:
  - "0"
---
<blockquote><header>
<h1>Announcing ggraph: A grammar of graphics for relational data</h1>
<h2 class="headline">FEBRUARY 23, 2017</h2>
</header><section id="post-body">I am absolutely thrilled to announce that <code class="highlighter-rouge">ggraph</code> has finally been released on CRAN. <code class="highlighter-rouge">ggraph</code> is my most ambitious package to date and its very early genesis has been described in a <a href="http://www.data-imaginist.com/2016/Becoming-the-intern/">prior post</a>. If any mention of <code class="highlighter-rouge">ggraph</code> is completely new to you, then in short terms <code class="highlighter-rouge">ggraph</code> is an extension of the <code class="highlighter-rouge">ggplot2</code> API to support relational data such as networks and trees. I feel fairly confident in saying that <code class="highlighter-rouge">ggraph</code> is the most powerful way to create static network based visualizations in R. Leading up to the release, the three main concepts of <code class="highlighter-rouge">ggraph</code> has been described in detail in their own blog posts (<a href="http://www.data-imaginist.com/2017/ggraph-introduction-layouts/">layouts</a>, <a href="http://www.data-imaginist.com/2017/ggraph-introduction-nodes/">nodes</a>, and <a href="http://www.data-imaginist.com/2017/ggraph-introduction-edges/">edges</a>) so this will not be reiterated here. Instead I’ll talk a bit about the philosophy behind the package as well as show of some of the features that do not fall into any of the three main concepts.
<h2 id="the-philosophy">The Philosophy</h2>
There is no shortage of software for creating network visualizations and there is no shortage of said visualizations themselves. Often though, the visualizations are more impressive than informative and it is easy to feel that their main task is to show that we are really dealing with some complex data. All of this has led to a certain disdain for classic network visualizations perfectly encapsulated in the nickname <em>hairballs</em>. It does not have to be like this! The greatness of <code class="highlighter-rouge">ggplot2</code> lies in how it allows users to quickly iterate over visualization approaches, thus better ensuring that the best visualization approach is reached. If this was extended to relational data it is my belief that users would be more likely to try to make plots that are more meaningful. After all we all want interpretability, right? Consider having to try out 7 different network visualization packages with different APIs versus just mixing and matching layouts and geoms in an iterative process — I know which way I prefer.

The goal of <code class="highlighter-rouge">ggraph</code> is thus clear — provide everything related to visualizations of relational data in a <code class="highlighter-rouge">ggplot2</code>-like API to lessen the cognitive load on experimenting with different visual representations. I’m not there yet, but I feel the current version represents a solid foundation where most users will not feel many limitations — on the contrary I believe most users will feel like the chains have come off and they are set free.
<h3 id="future-focus">Future focus</h3>
As I pointed out, <code class="highlighter-rouge">ggraph</code> is far from done. I’ll try to keep my development focus in the open by putting things on the road-map as <a href="https://github.com/thomasp85/ggraph/issues">GitHub issues</a>. Honorable mentions include matrix, d3-force and sankey layout, expanded support for edge endings (more choices than <code class="highlighter-rouge">grid::arrow()</code>provides), edge routing (avoid node collision), and textbox nodes. I welcome all suggestions as the world of network visualizations is moving fast and I cannot keep on top of everything.
<h2 id="features-besides-layouts-nodes-and-edges">Features besides layouts, nodes, and edges</h2>
Understanding the node and edge geoms along with how layouts are defined will get you a long way towards visualizing networks. Still, <code class="highlighter-rouge">ggraph</code> has more to offer, some of which will be discussed here:
<h3 id="theme_graph">theme_graph()</h3>
Consider the following plot:

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">library</span><span class="p">(</span><span class="n">ggraph</span><span class="p">)</span>
<span class="n">library</span><span class="p">(</span><span class="n">igraph</span><span class="p">)</span>
<span class="n">graph</span> <span class="o">&lt;-</span> <span class="n">graph_from_data_frame</span><span class="p">(</span><span class="n">highschool</span><span class="p">)</span>

<span class="n">p</span> <span class="o">&lt;-</span> <span class="n">ggraph</span><span class="p">(</span><span class="n">graph</span><span class="p">,</span> <span class="n">layout</span> <span class="o">=</span> <span class="s1">'kk'</span><span class="p">)</span> <span class="o">+</span> 
    <span class="n">geom_edge_link</span><span class="p">(</span><span class="n">aes</span><span class="p">(</span><span class="n">colour</span> <span class="o">=</span> <span class="n">factor</span><span class="p">(</span><span class="n">year</span><span class="p">)))</span> <span class="o">+</span> 
    <span class="n">geom_node_point</span><span class="p">()</span> <span class="o">+</span> 
    <span class="n">ggtitle</span><span class="p">(</span><span class="s1">'An example'</span><span class="p">)</span>
    
<span class="n">p</span></code></pre>
</figure><img src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-2-1-1.png" alt="center" />

While the <code class="highlighter-rouge">ggplot2</code> heritage clearly shows due to the grey background with white grid lines, the whole concept of x and y axes is often redundant in network visualizations and are just a distraction. <code class="highlighter-rouge">ggraph</code>provides its own theme optimized for network visualizations called <code class="highlighter-rouge">theme_graph()</code>, that facilitates clean and beautiful visualizations:

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">p</span> <span class="o">+</span> <span class="n">theme_graph</span><span class="p">()</span></code></pre>
</figure><img src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-3-1.png" alt="center" />

<code class="highlighter-rouge">theme_graph()</code>, besides removing axes, grids, and border, changes the font to <em>Arial Narrow</em> (this can be overridden). Furthermore, it makes it easy to change the coloring of the plot:

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">p</span> <span class="o">+</span> <span class="n">theme_graph</span><span class="p">(</span><span class="n">background</span> <span class="o">=</span> <span class="s1">'grey20'</span><span class="p">,</span> <span class="n">text_colour</span> <span class="o">=</span> <span class="s1">'white'</span><span class="p">)</span></code></pre>
</figure><img src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-4-1-1.png" alt="center" />

Adding the same theme to every plot is tedious and <code class="highlighter-rouge">ggraph</code> provides a way to avoid this. Using <code class="highlighter-rouge">set_graph_style()</code> the <code class="highlighter-rouge">theme_graph()</code> is set as default. As an extra benefit all text-based geoms gets their defaults updated so the text automatically uses the same style as the theme.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">set_graph_style</span><span class="p">()</span>

<span class="n">p</span></code></pre>
</figure><img src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-5-1-1.png" alt="center" />
<h3 id="facetting">Facetting</h3>
A powerful but underutilized way of gaining insight into networks is by using small multiples. This technique can reduce edge over-plotting in a very meaningful way by spreading nodes and edges out based on their attributes. The benefits of small multiples are not unique to relational data, as the popularity of <code class="highlighter-rouge">ggplot2</code>s facetting functionality shows. The base facetting functions provided by <code class="highlighter-rouge">ggplot2</code> is a bad fit for networks though, as we are working with two very distinct types of data. If you facet on a node attribute, all edges would be plotted in all panels, despite the terminal nodes not being present which is not what you expect. Because of this <code class="highlighter-rouge">ggraph</code> comes with its own set of facetting functions tailored to network data:
<h4 id="facet_nodes-and-facet_edges">facet_nodes() and facet_edges()</h4>
These two functions are equivalent to <code class="highlighter-rouge">facet_wrap()</code> in functionality, but they only address node and edge data respectively. When using <code class="highlighter-rouge">facet_nodes()</code> edges are only drawn in a panel if both terminal nodes are present there. When using <code class="highlighter-rouge">facet_edges()</code> nodes are always drawn in all panels even if the node data contains an attribute named the same as the one used for the edge facetting.

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="c1"># Assign each node to a random class
</span><span class="n">V</span><span class="p">(</span><span class="n">graph</span><span class="p">)</span><span class="o">$</span><span class="n">class</span> <span class="o">&lt;-</span> <span class="n">sample</span><span class="p">(</span><span class="nb">letters</span><span class="p">[</span><span class="m">1</span><span class="o">:</span><span class="m">4</span><span class="p">],</span> <span class="n">gorder</span><span class="p">(</span><span class="n">graph</span><span class="p">),</span> <span class="kc">TRUE</span><span class="p">)</span>
<span class="c1"># Make year a character
</span><span class="n">E</span><span class="p">(</span><span class="n">graph</span><span class="p">)</span><span class="o">$</span><span class="n">year</span> <span class="o">&lt;-</span> <span class="nf">as.character</span><span class="p">(</span><span class="n">E</span><span class="p">(</span><span class="n">graph</span><span class="p">)</span><span class="o">$</span><span class="n">year</span><span class="p">)</span>

<span class="n">p</span> <span class="o">&lt;-</span> <span class="n">ggraph</span><span class="p">(</span><span class="n">graph</span><span class="p">,</span> <span class="n">layout</span> <span class="o">=</span> <span class="s1">'kk'</span><span class="p">)</span> <span class="o">+</span> 
    <span class="n">geom_edge_fan</span><span class="p">(</span><span class="n">aes</span><span class="p">(</span><span class="n">alpha</span> <span class="o">=</span> <span class="n">..index..</span><span class="p">,</span> <span class="n">colour</span> <span class="o">=</span> <span class="n">year</span><span class="p">))</span> <span class="o">+</span> 
    <span class="n">geom_node_point</span><span class="p">(</span><span class="n">aes</span><span class="p">(</span><span class="n">shape</span> <span class="o">=</span> <span class="n">class</span><span class="p">))</span> <span class="o">+</span> 
    <span class="n">scale_edge_alpha</span><span class="p">(</span><span class="n">guide</span> <span class="o">=</span> <span class="s1">'none'</span><span class="p">)</span>

<span class="n">p</span> <span class="o">+</span> <span class="n">facet_edges</span><span class="p">(</span><span class="o">~</span><span class="n">year</span><span class="p">)</span></code></pre>
</figure><img src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-6-1-1.png" alt="center" />

Often, when working with small multiples it is nice to have some visual separation between each plot — setting a foreground color in <code class="highlighter-rouge">theme_graph()</code> will add strip background and border (you can also use the <code class="highlighter-rouge">th_foreground()</code> helper for this):

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">p</span> <span class="o">+</span> <span class="n">facet_nodes</span><span class="p">(</span><span class="o">~</span><span class="n">class</span><span class="p">)</span> <span class="o">+</span> <span class="n">th_foreground</span><span class="p">(</span><span class="n">foreground</span> <span class="o">=</span> <span class="s1">'grey80'</span><span class="p">,</span> <span class="n">border</span> <span class="o">=</span> <span class="kc">TRUE</span><span class="p">)</span></code></pre>
</figure><img src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-7-1-1.png" alt="center" />

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="c1"># Lets not have to add this everytime
</span><span class="n">set_graph_style</span><span class="p">(</span><span class="n">foreground</span> <span class="o">=</span> <span class="s1">'grey80'</span><span class="p">)</span></code></pre>
</figure>
<h4 id="facet_graph">facet_graph</h4>
Facetting on two variables simultaneously is very powerful and something that is supported in <code class="highlighter-rouge">ggplot2</code> with <code class="highlighter-rouge">facet_grid()</code>. In <code class="highlighter-rouge">ggraph</code>the same is possible using <code class="highlighter-rouge">facet_graph()</code> that takes the behavior of <code class="highlighter-rouge">facet_nodes()</code> and <code class="highlighter-rouge">facet_edges()</code> and combines them:

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">p</span> <span class="o">+</span> <span class="n">facet_graph</span><span class="p">(</span><span class="n">year</span> <span class="o">~</span> <span class="n">class</span><span class="p">)</span></code></pre>
</figure><img src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-8-1.png" alt="center" />

As with <code class="highlighter-rouge">facet_grid()</code> marginal plots are supported as well:

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="n">p</span> <span class="o">+</span> <span class="n">facet_graph</span><span class="p">(</span><span class="n">year</span> <span class="o">~</span> <span class="n">class</span><span class="p">,</span> <span class="n">margins</span> <span class="o">=</span> <span class="kc">TRUE</span><span class="p">)</span></code></pre>
</figure><img src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-9-1.png" alt="center" />

While the default is to put facet the rows on edges and the columns on nodes, this is free to change using the <code class="highlighter-rouge">row_type</code> and <code class="highlighter-rouge">col_type</code>arguments. There is nothing stopping you from facetting on the same type in each dimension either:

<figure class="highlight">
<pre><code class="language-r" data-lang="r"><span class="c1"># Facet edge by the class of their start node as well as year
</span><span class="n">p</span> <span class="o">+</span> <span class="n">facet_graph</span><span class="p">(</span><span class="n">year</span> <span class="o">~</span> <span class="n">node1.class</span><span class="p">,</span> <span class="n">col_type</span> <span class="o">=</span> <span class="s1">'edge'</span><span class="p">)</span></code></pre>
</figure><img src="http://the-r.kr/wp-content/uploads/2017/02/unnamed-chunk-10-1.png" alt="center" />

I hope I have convinced you that facetting in the context of relational data is both very easy, as well as extremely powerful. Avoiding the hairball is one of the prime goal of network visualizations and using small multiples is a fantastic way of cutting down on the number of nodes and edges while still getting the full picture.

</section></blockquote>
<blockquote>ggraph, a package for creating network and tree visualizations using the ggplot2 API has just been released on CRAN</blockquote>
소스: <em><a href="http://www.data-imaginist.com/2017/Announcing-ggraph/">Data Imaginist - Announcing ggraph: A grammar of graphics for relational data</a></em>