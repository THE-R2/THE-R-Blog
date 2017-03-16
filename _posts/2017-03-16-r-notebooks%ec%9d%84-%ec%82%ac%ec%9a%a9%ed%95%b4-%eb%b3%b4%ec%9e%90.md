---
ID: 1638
post_title: R Notebooks을 사용해 보자!
author: The-R
post_date: 2017-03-16 19:27:34
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/03/16/r-notebooks%ec%9d%84-%ec%82%ac%ec%9a%a9%ed%95%b4-%eb%b3%b4%ec%9e%90/'
published: true
inline_featured_image:
  - "0"
---
Today we’re excited to announce <a href="http://rmarkdown.rstudio.com/r_notebooks.html">R Notebooks</a>, which add a powerful notebook authoring engine to <a href="http://rmarkdown.rstudio.com/">R Markdown</a>. Notebook interfaces for data analysis have compelling advantages including the close association of code and output and the ability to intersperse narrative with computation. Notebooks are also an excellent tool for teaching and a convenient way to share analyses.

<img class="alignnone size-full wp-image-3190" src="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-3-42-44-pm.png" sizes="(max-width: 490px) 100vw, 490px" srcset="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-3-42-44-pm.png 490w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-21-at-3-42-44-pm.png?w=143&amp;h=150 143w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-21-at-3-42-44-pm.png?w=286&amp;h=300 286w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-21-at-3-42-44-pm.png 670w" alt="screen-shot-2016-09-21-at-3-42-44-pm" width="490" height="515" data-attachment-id="3190" data-permalink="https://blog.rstudio.org/2016/10/05/r-notebooks/screen-shot-2016-09-21-at-3-42-44-pm/" data-orig-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-3-42-44-pm.png" data-orig-size="670,704" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;&quot;,&quot;camera&quot;:&quot;&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;0&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="screen-shot-2016-09-21-at-3-42-44-pm" data-image-description="" data-medium-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-3-42-44-pm.png?w=286" data-large-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-3-42-44-pm.png?w=490" />

You can try out R Notebooks today in the <a href="https://www.rstudio.com/products/rstudio/download/preview/">RStudio Preview Release</a>.
<h2>Interactive R Markdown</h2>
As an authoring format, R Markdown bears many similarities to traditional notebooks like <a href="https://jupyter.org/">Jupyter</a> and <a href="http://beakernotebook.com/">Beaker</a>. However, code in notebooks is typically executed interactively, one cell at a time, whereas code in R Markdown documents is typically executed in batch.

R Notebooks bring the interactive model of execution to your R Markdown documents, giving you the capability to work quickly and iteratively in a notebook interface without leaving behind the plain-text tools and production-quality output you’ve come to rely on from R Markdown.
<table>
<tbody>
<tr>
<th></th>
<th>R Markdown Notebooks</th>
<th>Traditional Notebooks</th>
</tr>
<tr>
<td>Plain text representation</td>
<td>✓</td>
<td></td>
</tr>
<tr>
<td>Same editor/tools used for R scripts</td>
<td>✓</td>
<td></td>
</tr>
<tr>
<td>Works well with version control</td>
<td>✓</td>
<td></td>
</tr>
<tr>
<td>Focus on production output</td>
<td>✓</td>
<td></td>
</tr>
<tr>
<td>Output inline with code</td>
<td>✓</td>
<td>✓</td>
</tr>
<tr>
<td>Output cached across sessions</td>
<td>✓</td>
<td>✓</td>
</tr>
<tr>
<td>Share code and output in a single file</td>
<td>✓</td>
<td>✓</td>
</tr>
<tr>
<td>Emphasized execution model</td>
<td>Interactive &amp; Batch</td>
<td>Interactive</td>
</tr>
</tbody>
</table>
This video provides a bit more background and a demonstration of notebooks in action:

<span class="embed-youtube"><iframe class="youtube-player" src="https://www.youtube.com/embed/zNzZ1PfUDNk?version=3&amp;rel=1&amp;fs=1&amp;autohide=2&amp;showsearch=0&amp;showinfo=1&amp;iv_load_policy=1&amp;wmode=transparent" width="560" height="315" allowfullscreen="allowfullscreen" data-mce-fragment="1"></iframe></span>
<div id="iterate-quickly" class="section level2">
<h2>Iterate Quickly</h2>
In a typical R Markdown document, you must re-knit the document to see your changes, which can take some time if it contains non-trivial computations. R Notebooks, however, let you run code and see the results in the document immediately. They can include just about any kind of content R produces, including console output, plots, data frames, and interactive <a href="http://www.htmlwidgets.org/">HTML widgets</a>.

<img class="alignnone size-full wp-image-3144" src="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-20-at-4-16-47-pm.png" sizes="(max-width: 476px) 100vw, 476px" srcset="https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-20-at-4-16-47-pm.png 476w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-20-at-4-16-47-pm.png?w=150 150w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-20-at-4-16-47-pm.png?w=300 300w" alt="screen-shot-2016-09-20-at-4-16-47-pm" data-attachment-id="3144" data-permalink="https://blog.rstudio.org/2016/10/05/r-notebooks/screen-shot-2016-09-20-at-4-16-47-pm/" data-orig-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-20-at-4-16-47-pm.png" data-orig-size="476,422" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;&quot;,&quot;camera&quot;:&quot;&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;0&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="screen-shot-2016-09-20-at-4-16-47-pm" data-image-description="" data-medium-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-20-at-4-16-47-pm.png?w=300" data-large-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-20-at-4-16-47-pm.png?w=476" />

You can see the progress of the code as it runs:

<img class="alignnone size-full wp-image-3184" src="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-10-52-02-am.png" sizes="(max-width: 474px) 100vw, 474px" srcset="https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-21-at-10-52-02-am.png 474w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-21-at-10-52-02-am.png?w=150 150w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-21-at-10-52-02-am.png?w=300 300w" alt="screen-shot-2016-09-21-at-10-52-02-am" data-attachment-id="3184" data-permalink="https://blog.rstudio.org/2016/10/05/r-notebooks/screen-shot-2016-09-21-at-10-52-02-am/" data-orig-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-10-52-02-am.png" data-orig-size="474,307" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;&quot;,&quot;camera&quot;:&quot;&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;0&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="screen-shot-2016-09-21-at-10-52-02-am" data-image-description="" data-medium-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-10-52-02-am.png?w=300" data-large-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-10-52-02-am.png?w=474" />

You can preview the results of individual inline expressions, too:

<img class="alignnone size-full wp-image-3149" src="http://the-r.kr/wp-content/uploads/2017/03/notebook-inline-output.png" sizes="(max-width: 196px) 100vw, 196px" srcset="https://rstudioblog.files.wordpress.com/2016/09/notebook-inline-output.png 196w, https://rstudioblog.files.wordpress.com/2016/09/notebook-inline-output.png?w=150 150w" alt="notebook-inline-output" data-attachment-id="3149" data-permalink="https://blog.rstudio.org/2016/10/05/r-notebooks/notebook-inline-output/" data-orig-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-inline-output.png" data-orig-size="196,95" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;&quot;,&quot;camera&quot;:&quot;&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;0&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="notebook-inline-output" data-image-description="" data-medium-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-inline-output.png?w=196" data-large-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-inline-output.png?w=196" />

Even your LaTeX equations render in real-time as you type:

<img class="alignnone size-full wp-image-3111" src="http://the-r.kr/wp-content/uploads/2017/03/notebook-mathjax.png" sizes="(max-width: 477px) 100vw, 477px" srcset="https://rstudioblog.files.wordpress.com/2016/09/notebook-mathjax.png 477w, https://rstudioblog.files.wordpress.com/2016/09/notebook-mathjax.png?w=150 150w, https://rstudioblog.files.wordpress.com/2016/09/notebook-mathjax.png?w=300 300w" alt="notebook-mathjax" data-attachment-id="3111" data-permalink="https://blog.rstudio.org/2016/10/05/r-notebooks/notebook-mathjax/" data-orig-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-mathjax.png" data-orig-size="477,133" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;&quot;,&quot;camera&quot;:&quot;&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;0&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="notebook-mathjax" data-image-description="" data-medium-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-mathjax.png?w=300" data-large-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-mathjax.png?w=477" />

This focused mode of interaction doesn’t require you to keep the console, viewer, or output panes open. Everything you need is at your fingertips in the editor, reducing distractions and helping you concentrate on your analysis. When you’re done, you’ll have a formatted, reproducible record of what you’ve accomplished, with plenty of context, perfect for your own records or sharing with others.

</div>
<div id="batteries-included" class="section level2">
<h2>Batteries Included</h2>
R Notebooks can run more than just R code. You can run chunks <a href="http://rmarkdown.rstudio.com/authoring_knitr_engines.html">written in other languages</a>, like Python, Bash, or C++ (Rcpp).

<img class="alignnone size-full wp-image-3147" src="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-20-at-4-25-48-pm.png" sizes="(max-width: 475px) 100vw, 475px" srcset="https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-20-at-4-25-48-pm.png 475w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-20-at-4-25-48-pm.png?w=150 150w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-20-at-4-25-48-pm.png?w=300 300w" alt="screen-shot-2016-09-20-at-4-25-48-pm" data-attachment-id="3147" data-permalink="https://blog.rstudio.org/2016/10/05/r-notebooks/screen-shot-2016-09-20-at-4-25-48-pm/" data-orig-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-20-at-4-25-48-pm.png" data-orig-size="475,190" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;&quot;,&quot;camera&quot;:&quot;&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;0&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="screen-shot-2016-09-20-at-4-25-48-pm" data-image-description="" data-medium-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-20-at-4-25-48-pm.png?w=300" data-large-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-20-at-4-25-48-pm.png?w=475" />

It’s even possible to run SQL directly:

<img class="alignnone size-full wp-image-3114" src="http://the-r.kr/wp-content/uploads/2017/03/notebook-sql.png" sizes="(max-width: 490px) 100vw, 490px" srcset="http://the-r.kr/wp-content/uploads/2017/03/notebook-sql.png 490w, https://rstudioblog.files.wordpress.com/2016/09/notebook-sql.png?w=150 150w, https://rstudioblog.files.wordpress.com/2016/09/notebook-sql.png?w=300 300w, https://rstudioblog.files.wordpress.com/2016/09/notebook-sql.png 582w" alt="notebook-sql" data-attachment-id="3114" data-permalink="https://blog.rstudio.org/2016/10/05/r-notebooks/notebook-sql/" data-orig-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-sql.png" data-orig-size="582,363" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;&quot;,&quot;camera&quot;:&quot;&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;0&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="notebook-sql" data-image-description="" data-medium-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-sql.png?w=300" data-large-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-sql.png?w=490" />

This makes an R Notebook an excellent tool for orchestrating a reproducible, end-to-end data analysis workflow; you can easily ingest data using your tool of choice, and share data among languages by using packages like <a href="https://cran.r-project.org/web/packages/feather/index.html">feather</a>, or ordinary CSV files.
<h2>Reproducible Notebooks</h2>
While you can run chunks (and even individual lines of R code!) in any order you like, a fully reproducible document must be able to be re-executed start-to-finish in a clean environment. There’s a built-in command to do this, too, so it’s easy to test your notebooks for reproducibility.

<img class="alignnone size-full wp-image-3192" src="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-3-52-34-pm.png" sizes="(max-width: 252px) 100vw, 252px" srcset="https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-21-at-3-52-34-pm.png 252w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-21-at-3-52-34-pm.png?w=136 136w" alt="screen-shot-2016-09-21-at-3-52-34-pm" data-attachment-id="3192" data-permalink="https://blog.rstudio.org/2016/10/05/r-notebooks/screen-shot-2016-09-21-at-3-52-34-pm/" data-orig-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-3-52-34-pm.png" data-orig-size="252,277" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;&quot;,&quot;camera&quot;:&quot;&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;0&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="screen-shot-2016-09-21-at-3-52-34-pm" data-image-description="" data-medium-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-3-52-34-pm.png?w=252" data-large-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-21-at-3-52-34-pm.png?w=252" />
<h2>Rich Output Formats</h2>
Since they’re built on R Markdown, R Notebooks work seamlessly with other R Markdown output types. You can use any existing R Markdown document as a notebook, or render (knit) a notebook to any R Markdown output type.

<img class="alignnone size-full wp-image-3117" src="http://the-r.kr/wp-content/uploads/2017/03/notebook-yaml.png" sizes="(max-width: 277px) 100vw, 277px" srcset="https://rstudioblog.files.wordpress.com/2016/09/notebook-yaml.png 277w, https://rstudioblog.files.wordpress.com/2016/09/notebook-yaml.png?w=150 150w" alt="notebook-yaml" data-attachment-id="3117" data-permalink="https://blog.rstudio.org/2016/10/05/r-notebooks/notebook-yaml/" data-orig-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-yaml.png" data-orig-size="277,187" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;&quot;,&quot;camera&quot;:&quot;&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;0&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="notebook-yaml" data-image-description="" data-medium-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-yaml.png?w=277" data-large-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-yaml.png?w=277" />

The same document can be used as a notebook when you’re quickly iterating on ideas and later rendered to a wholly different format for publication – no duplication of code, data, or output required.

</div>
<div id="share-and-publish" class="section level2">
<h2>Share and Publish</h2>
R Notebooks are easy to share with collaborators. Because they’re plain-text files, they work well with version control systems like Git. Your collaborators don’t even need RStudio to edit them, since notebooks can be <a href="http://rmarkdown.rstudio.com/r_notebook_format.html">rendered in the R console</a> using the open source <a href="https://cran.r-project.org/web/packages/rmarkdown/index.html">rmarkdown</a> package.

Rendered notebooks can be previewed right inside RStudio:

<img class="alignnone size-full wp-image-3150" src="http://the-r.kr/wp-content/uploads/2017/03/notebook-preview.png" sizes="(max-width: 490px) 100vw, 490px" srcset="http://the-r.kr/wp-content/uploads/2017/03/notebook-preview.png 490w, https://rstudioblog.files.wordpress.com/2016/09/notebook-preview.png?w=980&amp;h=810 980w, https://rstudioblog.files.wordpress.com/2016/09/notebook-preview.png?w=150&amp;h=124 150w, https://rstudioblog.files.wordpress.com/2016/09/notebook-preview.png?w=300&amp;h=248 300w, https://rstudioblog.files.wordpress.com/2016/09/notebook-preview.png?w=768&amp;h=634 768w" alt="notebook-preview" width="490" height="405" data-attachment-id="3150" data-permalink="https://blog.rstudio.org/2016/10/05/r-notebooks/notebook-preview/" data-orig-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-preview.png" data-orig-size="1136,938" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;&quot;,&quot;camera&quot;:&quot;&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;0&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="notebook-preview" data-image-description="" data-medium-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-preview.png?w=300" data-large-file="http://the-r.kr/wp-content/uploads/2017/03/notebook-preview.png?w=490" />

While the notebook preview looks similar to a rendered R Markdown document, the notebook preview does not execute any of your R code chunks; it simply shows you a rendered copy of the markdown in your document along with the most recent chunk output. Because it’s very fast to generate this preview (again, no R code is executed), it’s generated every time you save the R Markdown document.

The generated HTML file has the special extension <em>.nb.html</em>. It is self-contained, free of dependencies, and can be viewed locally or published to any static web hosting service.

<img class="alignnone size-full wp-image-3127" src="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-14-at-12-12-35-pm.png" sizes="(max-width: 490px) 100vw, 490px" srcset="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-14-at-12-12-35-pm.png 490w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-14-at-12-12-35-pm.png?w=146 146w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-14-at-12-12-35-pm.png?w=292 292w, https://rstudioblog.files.wordpress.com/2016/09/screen-shot-2016-09-14-at-12-12-35-pm.png 642w" alt="screen-shot-2016-09-14-at-12-12-35-pm" data-attachment-id="3127" data-permalink="https://blog.rstudio.org/2016/10/05/r-notebooks/screen-shot-2016-09-14-at-12-12-35-pm/" data-orig-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-14-at-12-12-35-pm.png" data-orig-size="642,659" data-comments-opened="1" data-image-meta="{&quot;aperture&quot;:&quot;0&quot;,&quot;credit&quot;:&quot;&quot;,&quot;camera&quot;:&quot;&quot;,&quot;caption&quot;:&quot;&quot;,&quot;created_timestamp&quot;:&quot;0&quot;,&quot;copyright&quot;:&quot;&quot;,&quot;focal_length&quot;:&quot;0&quot;,&quot;iso&quot;:&quot;0&quot;,&quot;shutter_speed&quot;:&quot;0&quot;,&quot;title&quot;:&quot;&quot;,&quot;orientation&quot;:&quot;0&quot;}" data-image-title="screen-shot-2016-09-14-at-12-12-35-pm" data-image-description="" data-medium-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-14-at-12-12-35-pm.png?w=292" data-large-file="http://the-r.kr/wp-content/uploads/2017/03/screen-shot-2016-09-14-at-12-12-35-pm.png?w=490" />

It also includes a bundled copy of the R Markdown source file, so it can be seamlessly opened in RStudio to resume work on the notebook with all output intact.
<h2>Try It Out</h2>
To try out R Notebooks, you’ll need to download the latest <a href="https://www.rstudio.com/products/rstudio/download/preview/">RStudio Preview Release</a>.

You can find documentation on notebook features on the <a href="http://rmarkdown.rstudio.com/r_notebooks.html">R Notebooks</a> page on the R Markdown website, and we’ve also published a video tutorial in our <a href="https://www.rstudio.com/resources/webinars/introducing-notebooks-with-r-markdown/">R Notebooks Webinar</a>.

We believe the R Notebook will become a powerful new addition to your toolkit. Give it a spin and let us know what you think!

</div>
소스: <em><a href="https://blog.rstudio.org/2016/10/05/r-notebooks/">R Notebooks | RStudio Blog</a></em>