---
ID: 1951
post_title: 'R 코딩의 모범 사례 : R 방식을 쓰고 있습니다!'
author: The-R
post_date: 2017-04-14 10:51:18
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/04/14/r-%ec%bd%94%eb%94%a9%ec%9d%98-%eb%aa%a8%eb%b2%94-%ec%82%ac%eb%a1%80-r-%eb%b0%a9%ec%8b%9d%ec%9d%84-%ec%93%b0%ea%b3%a0-%ec%9e%88%ec%8a%b5%eb%8b%88%eb%8b%a4/'
published: true
inline_featured_image:
  - "0"
---
<img class="aligncenter size-full wp-image-8045" src="http://the-r.kr/wp-content/uploads/2017/04/R-Best-Practices-R-you-writing-the-R-way-1.jpg" sizes="(max-width: 1200px) 100vw, 1200px" alt="" width="450" height="236" data-recalc-dims="1" data-lazy-loaded="true" />

By <a href="https://www.linkedin.com/in/milind-paradkar-b37292107/" target="_blank" rel="nofollow">Milind Paradkar</a>

모든 프로그래머는 불가피하게 일상 업무에 수많은 코드를 씁니다. 그러나 모든 프로그래머가 다른 사람들이 쉽게 이해할 수있는 깨끗한 코드를 작성하는 습관을 갖지는 않습니다. 그 이유 중 하나는 프로그래머가 프로그램을 작성하는 데 따르는 모범 사례에 대한 인식 부족 때문일 수 있습니다. 초보자 프로그래머에게는 특히 그렇습니다. 이 글에서는 코드 가독성, 일관성 및 반복성 향상으로 이어질 R 프로그래밍 우수 사례를 소개합니다. 한번 읽어 보세요!

&nbsp;
<h3><strong>R로 작성하는 모범 사례</strong></h3>
<strong>1) 코드에 대한 설명</strong>

코딩을 시작할 때 R 코드가 맨 처음 행에서 무엇을하는지 설명하십시오. 후속 코드 블록의 경우 블록을 설명하는 동일한 방법을 따릅니다. 이렇게하면 다른 사람들이 코드를 이해하고 사용하기가 쉬워집니다.

<strong>예제:</strong>
<pre class=""># 이 코드는 52주간의 주가의 높은 효과를 포착 함
# OOO가 개발한 코드 임</pre>
<strong>2) 패키지 로드</strong>

첫 번째 줄에 코드를 설명하고 나면 라이브러리 함수를 사용하여 코드를 실행하는 데 필요한 모든 관련 R 패키지를 나열하고 로드 하십시오.

<strong>예제:</strong>
<pre class="">library(quantmod);  library(zoo); library(xts);
library(PerformanceAnalytics); library(timeSeries); library(lubridate);</pre>
<strong>3) 업데이트된 패키지를 사용 하세요</strong>

코딩하는 동안 최신 업데이트 된 R 패키지를 사용하고 있는지 확인하십시오. R 패키지의 버전을 확인하려면 packageVersion 함수를 사용할 수 있습니다.

<strong>예제:</strong>
<pre class="">packageVersion("TTR")
[1] ‘0.23.1’</pre>
<strong>4) 동일한 폴더에 모든 소스 파일 구성</strong>

사용될 모든 필요한 파일을 저장하세요. 각각의 상대 경로를 사용하여 액세스 할 수 있습니다.

<strong>예제:</strong>
<pre class=""># Reading file using relative path
df = read.csv(file = "NIFTY.csv", header = TRUE)

# Reading file using full path
df =  read.csv(file = "C:/Users/Documents/NIFTY.csv", header = TRUE)</pre>
<strong>5) Use a consistent style for data structure types – </strong>R programming language allows for different data structures like vectors, factors, data frames, matrices, and lists. Use a similar naming for a particular type of data structure. This will make it easy to recognize the similar data structures used in the code and to spot the problems easily.

<strong>Example:</strong>
You can name all different data frames used in your code by adding .df as the suffix.
<pre class="">aapl.df   = as.data.frame(read.csv(file = "AAPL.csv", header = TRUE))
amzn.df = as.data.frame(read.csv(file = "AMZN.csv", header = TRUE))
csco.df  = as.data.frame(read.csv(file = "CSCO.csv", header = TRUE))</pre>
<strong>6) Indent your code </strong>– Indentation makes your code easier to read, especially, if there are multiple nested statements like For-loop and If statement.

<strong>Example:</strong>
<pre class=""># Computing the Profit &amp; Loss (PL) and the Equity
dt$PL = numeric(nrow(dt))
for (i in 1:nrow(dt)){
   if (dt$Signal[i] == 1) {dt$PL[i+1] = dt$Close[i+1] - dt$Close[i]}
   if (dt$Signal[i] == -1){dt$PL[i+1] = dt$Close[i] - dt$Close[i+1]}
}</pre>
<strong>7) Remove temporary objects –</strong> For long codes, running in thousands of lines, it is a good practice to remove temporary objects after they have served their purpose in the code. This can ensure that R does not into memory issues.

<strong>8) Time the code – </strong>You can time your code using the system.time function. You can also use the same function to find out the time taken by different blocks of code. The function returns the amount of time taken in seconds to evaluate the expression or a block of code. Timing codes will help to figure out any bottlenecks and help speed up your codes by making the necessary changes in the script.

To find the time taken for different blocks we wrapped them in curly braces within the call to the system.time function.

The two important metrics returned by the function include:
i) User time – time charged to the CPU(s) for the code
ii) Elapsed time – the amount of time elapsed to execute the code in entirety

<strong> </strong><strong>Example:</strong>
<pre class=""># Generating random numbers
system.time({
mean_1 = rnorm(1e+06, mean = 0, sd = 0.8)
})

user    system    elapsed
0.40      0.00       0.45</pre>
<strong>9) Use vectorization –</strong> Vectorization results in faster execution of codes, especially when we are dealing with large data sets. One can use statements like the ifelse statement or the with function for vectorization.

<strong>Example:</strong>
Consider the NIFTY 1-year price series. Let us find the gap opening for each day using both the methods (using for-loop and with function) and time them using the system.time function. Note the time taken to execute the for-loop versus the time to execute the with function in combination with the lagpad function.
<pre class="">library(quantmod)
# Using FOR Loop
system.time({
df = read.csv("NIFTY.csv")
df = df[,c(1,3:6)]
df$GapOpen = double(nrow(df))
for ( i in 2:nrow(df)) {
df$GapOpen[i] = round(Delt(df$CLOSE[i-1],df$OPEN[i])*100,2)
}
print(head(df))
})</pre>
<img class="size-full wp-image-8054 alignnone" src="http://the-r.kr/wp-content/uploads/2017/04/R-Best-Practices-Blog_Pic1.png" sizes="(max-width: 666px) 100vw, 666px" alt="" width="450" height="133" data-lazy-loaded="true" />
<pre class=""># Using with function + lagpad, instead of FOR Loop
system.time({
df = read.csv("NIFTY.csv")
df = dt[,c(1,3:6)]

lagpad = function(x, k) {
c(rep(NA, k), x)[1 : length(x)]
}

df$PrevClose = lagpad(df$CLOSE, 1)
df$GapOpen_ = with(df, round(Delt(df$PrevClose,df$OPEN)*100,2))
print(head(df))
})</pre>
<img class="size-full wp-image-8058 alignnone" src="http://the-r.kr/wp-content/uploads/2017/04/R-Best-Practices-Blog_Pic2.png" sizes="(max-width: 665px) 100vw, 665px" alt="" width="450" height="131" data-lazy-loaded="true" />

<strong>10) Folding codes </strong>– Folding codes is a way wherein the R programmer can fold a code of line or code sections. This allows hiding blocks of code whenever required, and makes it easier to navigate through lengthy codes. Code folding can be done in two ways:
i) Automatic folding of codes
ii) User-defined folding of codes

<strong>Automatic folding of codes: </strong>RStudio automatically provides the flexibility to fold the codes. When a coder writes a function or conditional blocks, RStudio automatically creates foldable codes.

<strong>User-defined folding of codes: </strong>
One can also fold a random group of codes by using Edit -&gt; Folding -&gt; Collapse or by simply selecting the group of codes and pressing Alt+L key.

<strong>User-defined folding can also be done via Code Sections:</strong>
To insert a new code section you can use the Code -&gt; Insert Section command. Alternatively, any comment line which includes at least four trailing dashes (-), equal signs (=) or pound signs (#) automatically creates a code section.

<img class="aligncenter wp-image-8061" src="http://the-r.kr/wp-content/uploads/2017/04/R-Best-Practices-Blog_Pic3-1.png" sizes="(max-width: 541px) 100vw, 541px" alt="" width="450" height="264" data-lazy-loaded="true" />

<strong>11) Review and test your code rigorously – </strong>Once your code is ready, ensure that you test it code rigorously on different input parameters. Ensure that the logic used in statements like for-loop, if statement, ifelse statement is correct. It is a nice idea to get your code reviewed by your colleague to ensure that the work is of high quality.

<strong>12) Don’t save your workspace</strong> <strong>–</strong> When you want to exit R it checks if you want to save your workspace. It is advisable to not save the workspace and start in a clean workspace for your next R session. Objects from the previous R sessions can lead to errors which can be hard to debug.

<img class="aligncenter size-full wp-image-8063" src="http://the-r.kr/wp-content/uploads/2017/04/R-Best-Practices-Blog_Pic4.png" sizes="(max-width: 437px) 100vw, 437px" srcset="http://the-r.kr/wp-content/uploads/2017/04/R-Best-Practices-Blog_Pic4.png" alt="" width="437" height="135" data-lazy-loaded="true" />

These were some of the best practices of writing in R that one can follow to make your codes easy to read, debug and to ensure consistency.
<h3><strong> </strong><strong>Next Step</strong></h3>
<strong> </strong>If you want to learn various aspects of <a href="https://www.quantinsti.com/" target="_blank" rel="nofollow">Algorithmic trading</a> then check out the <a href="https://www.quantinsti.com/epat/" target="_blank" rel="nofollow">Executive Programme in Algorithmic Trading (EPAT™)</a>. The course covers training modules like Statistics &amp; Econometrics, Financial Computing &amp; Technology, and Algorithmic &amp; Quantitative Trading. EPAT™ equips you with the required skill sets to be a successful trader. <a href="https://www.quantinsti.com/epat/" target="_blank" rel="nofollow">Enroll now</a>!

The post <a href="https://www.quantinsti.com/blog/r-best-practices-r-you-writing-the-r-way/" target="_blank" rel="nofollow">R Best Practices: R you writing the R way!</a> appeared first on .

소스: <em><a href="https://www.r-bloggers.com/r-best-practices-r-you-writing-the-r-way/">R Best Practices: R you writing the R way! | R-bloggers</a></em>