---
ID: 1665
post_title: >
  엘라스틱 서치(Elasticsearch)
  소개
author: The-R
post_date: 2017-03-18 13:30:39
post_excerpt: ""
layout: post
permalink: 'http://the-r.kr/2017/03/18/%ec%97%98%eb%9d%bc%ec%8a%a4%ed%8b%b1-%ec%84%9c%ec%b9%98elasticsearch-%ec%86%8c%ea%b0%9c/'
published: true
inline_featured_image:
  - "0"
---
소스: <em><a href="http://navercast.naver.com/contents.nhn?rid=122&amp;contents_id=127228&amp;leafId=122">엘라스틱 서치(Elasticsearch) : 네이버캐스트</a></em>

&nbsp;
<p class="t_txt">데이터과학이 발전하면서 함께 성장하고 있는 기술이 있었으니, 바로 오픈소스 기술이다. 데이터 기술은 저장, 정제, 시각화, 분석 등 그 종류가 다양하며, 각 카테고리에서 수십 개의 오픈소스 데이터 기술이 서로 경쟁하고 있다. 이 가운데 ‘엘라스틱서치’는 검색 분야에서 큰 주목을 받고 있으며, 최근 들어 오픈소스 스타트업으로서 성과도 내고 있어 영향력이 커지고 있다.</p>

<div class="t_ptype btn_img_zoom">
<div class="edtitor_img_uio"><span class="img_wrap2"><img title="" src="http://the-r.kr/wp-content/uploads/2017/03/01.png" alt="" data-src="http://ncc.phinf.naver.net/20161207_249/1481071937362T8oCX_PNG/b01.png" /></span>
<p class="cap">엘라스틱 로고</p>

</div>
</div>
<a name="toc1"></a>
<div class="t_lv_tit">
<h4>아내의 요리법 검색 기술에서 엘라스틱서치까지</h4>
</div>
<p class="t_txt">엘라스틱서치는 엘라스틱의 대표 기술이다. 원래 초창기 기업 이름도 엘라스틱서치였지만, 서비스 영역이 확장되면서 2015년 사명을 엘라스틱으로 변경했다. 엘라스틱서치는 이름에서 유추할 수 있듯이, 검색기술이다. ‘아파치 루신(<span class="word_dic en">Apache</span> <span class="word_dic en">Lucene</span>)’을 기반으로 만든 분산 검색엔진으로, 설치와 서버 확장이 편리한 것으로 유명한 기술이다. 대표적으로 깃허브, 이베이, 가디언 같은 기업이 엘라스틱서치 기술로 내부 검색 기능을 구축했다.</p>

<div class="t_ptype5">
<div class="edtitor_img_uio"><span class="img_wrap2"><img src="http://the-r.kr/wp-content/uploads/2017/03/02-1.jpg" alt="" /></span>
<p class="cap">샤이 배넌 엘라스틱서치 창시자. 현재는 엘라스틱에서 <span class="word_dic en">CTO</span> 직을 맡고 있다. &lt;출처: 엘라스틱 홈페이지&gt;</p>

</div>
</div>
<p class="t_txt">엘라스틱서치의 탄생은 자상한 남편의 이야기로 시작한다. 엘라스틱 공동 설립자이자 현재 <span class="word_dic en">CTO</span> 직을 맡고 있는 샤이 배넌(<span class="word_dic en">Shay</span> <span class="word_dic en">Banon</span>)은 2004년, 런던으로 이사를 가야 했다. 당시 그의 아내가 요리사의 길을 준비하고 있어 이를 지원해주기 위해서였다. 새로운 곳으로 이사를 하다 보니 샤이 배넌은 개발자로서 새 직장을 구하는 데 시간이 필요했고, 자연스레 집에 있는 시간이 많았다. 그는 새로운 기술을 공부하면서 남는 시간을 보냈는데, 마침 그의 아내는 요리 수업 시간에 배워온 자료를 정리하고 있었다. 그런 모습을 본 샤이 배넌은 아내에게 맞춤화된 요리법 검색 서비스를 만들어주기로 결심했다. 그때 발견한 기술이 바로 ‘루신’이다. 루신은 자바에서 사용할 수 있는 검색 기술 라이브러리로, 당시 꽤 유명한 오픈소스 기술이었다. 샤이 배넌은 루신을 기반으로 필요한 검색 기능을 구축하기 시작했고, 자체 오픈소스 기술인 ‘컴파스(<span class="word_dic en">Compass</span>)’를 개발하게 한다.</p>
<p class="t_txt">컴파스에 투자한 지 몇 달이 지나자, 샤이 배넌은 해당 기술이 요리법 검색 이상으로 활용될 수 있다는 것을 깨달았다. 검색 기술을 적용할 수 있는 분야는 무궁무진했기 때문이다. 실제로 현재 엘라스틱 고객군은 금융, 미디어, 유통, <span class="word_dic en">IT</span> 등 다양하다.</p>
<p class="t_txt">컴파스를 기반으로 조금 더 정교하게 만들어진 기술이 바로 엘라스틱서치다. 샤이 배넌은 취업 후 틈틈이 엘라스틱서치를 개발했지만, 그 성장 속도는 생각보다 빨랐다. 그는 아예 직장을 그만두고 엘라스틱서치에만 집중하기로 했다. 그러면서 뜻이 맞는 다른 개발자 3명과 함께 엘라스틱서치란 스타트업을 설립하게 된다. 아내를 위해 만들려던 요리검색 기술은 엘라스틱서치에 집중하느라 결국 완성하지 못했다고 한다.</p>
<a name="toc2"></a>
<div class="t_lv_tit">
<h4>오픈소스 기술이라는 무기</h4>
</div>
<p class="t_txt">엘라스틱서치의 기초 기술이었던 루신과 컴파스는 오픈소스 기술이다. 엘라스틱서치도 자연스레 오픈소스 기술로 배포됐다. 엘라스틱에서 제공하는 핵심 기술은 대부분 오픈소스 기술이며, 공동설립자들은 오픈소스 기술에 깊이 관여하는 개발자다. 그만큼 엘라스틱은 오픈소스 기술 친화적인 기업이다.</p>

<div class="t_ptype btn_img_zoom">
<div class="edtitor_img_uio"><span class="img_wrap2"><img title="" src="http://the-r.kr/wp-content/uploads/2017/03/03.png" alt="" data-src="http://ncc.phinf.naver.net/20161207_221/1481072360459L9CxP_PNG/b03.png" /></span>
<p class="cap">엘라스틱의 주요 기술은 오픈소스 기술로 구성돼 있다. &lt;출처: 엘라스틱 홈페이지&gt;</p>

</div>
</div>
<p class="t_txt">오픈소스 기술의 인기는 이전부터 높긴 하지만, 오픈소스 기술로 기업을 운영하고 수익을 얻는 것은 쉽지 않다. 그럼에도 불구하고 샤이 배넌은 오픈소스 기술 기업으로 엘라스틱을 성장시키겠다는 마음이 컸다고 한다. 그는 인터뷰에서 “오픈소스 형태로 기술을 공개하면 더 많은 곳에 더 빨리 퍼질 수 있다”라며 “이미 많은 혁신적인 기술들이 현재 오픈소스 기술로부터 나오고 있으며, 오픈소스 기술이 미래에 가야 할 방향이라고 생각했다”라고 밝히기도 했다. 또한 오픈소스 기술에서 얻은 노하우를 상용 제품에 적용하는 과정이 실제로 기업에 도움이 되기도 했다고 한다.</p>
<p class="t_txt">엘라스틱은 2012년 설립된 이후 3년 동안 해마다 투자를 유치했다. 투자금은 총 1억400만 달러, 우리 돈으로 약 1221억 원 규모였다. 그만큼 시장에서 엘라스틱의 가능성을 높게 본 셈이다. 샤이 배넌은 “라이브러리 정도의 오픈소스 기술이었다면 원하는 만큼 수익을 낼 수 없었을 것”이라며 “하지만 그보다 좀 더 크고 중요한 기술이라면 수익을 만들 수 있다고 생각했으며, 특히 데이터 양이 늘어날수록 검색의 힘은 더 강력해질 거라고 믿었다”라고 설립 계기를 밝혔다.</p>
<p class="t_txt">그 예상은 적중했다. 2010년 이후 많은 기업들이 데이터에서 가치를 찾아내기 위해 관련 기술을 구입하고 비용을 내고 있다. 엘라스틱도 기업용 제품으로 꾸준히 수익을 내는 중이다.</p>
<a name="toc3"></a>
<div class="t_lv_tit">
<h4>엘라스틱의 대표 기술 3인방, <span class="word_dic en">ELK</span></h4>
</div>
<p class="t_txt">엘라스틱은 현재 12개의 제품을 제공하고 있다. 이 중 가장 인기 있는 제품은 엘라스틱서치(<span class="word_dic en">Elasticsearch</span>), 로그스태시(<span class="word_dic en">Logstash</span>), 키바나(<span class="word_dic en">Kibana</span>)다. 이 세 기술은 앞글자를 따서 ‘<span class="word_dic en">ELK</span> 스택’이라고 불리기도 한다. 이용자는 3가지 제품을 조합해 데이터 수집부터 분석, 시각화를 통합적으로 작업할 수 있다.</p>
<p class="t_txt">먼저 엘라스틱서치는 분산형 레스트풀(<span class="word_dic en">RESTful</span>) 검색 및 분석 엔진이다. 정형, 비정형, 위치정보, 메트릭 등 원하는 방법으로 다양한 유형의 검색을 수행하고 결합할 수 있다. 가장 큰 장점은 확장성과 쉬운 설치다. 작은 규모로 적용해도 이후 점차 쉽게 확대할 수 있으며, <span class="word_dic en">API</span> 등을 이용해 구조를 단순화하고 설치하기 쉽다.</p>

<div class="t_ptype btn_img_zoom">
<div class="edtitor_img_uio"><span class="img_wrap2"><img title="" src="http://the-r.kr/wp-content/uploads/2017/03/04.png" alt="" data-src="http://ncc.phinf.naver.net/20161207_291/1481072535175c6wGP_PNG/b04.png" /></span>
<p class="cap">엘라스틱서치 예제 &lt;출처: 엘라스틱 홈페이지&gt;</p>

</div>
</div>
<p class="t_txt">로그스태시는 오픈소스 서버측 데이터 처리 파이프라인이다. 다양한 소스에서 동시에 데이터를 수집해 변환한 뒤 자주 사용하는 특정 보관소로 데이터를 보내는 역할을 한다. 데이터 이동 중에 구문 분석 및 변환이 가능해 분석을 쉽고 빠르게 하는 데 도움을 주며, 200개 이상의 플러그인을 지원해 다양한 기술과 조합해 사용할 수 있다.</p>

<div class="t_ptype">
<div class="edtitor_img_uio"><span class="img_wrap2"><img src="http://the-r.kr/wp-content/uploads/2017/03/05.png" alt="" /></span>
<p class="cap">로그스태시의 입력(<span class="word_dic en">input</span>) → 필터(<span class="word_dic en">filter</span>) → 출력(<span class="word_dic en">output</span>) 구조도 &lt;출처: 엘라스틱 홈페이지&gt;</p>

</div>
</div>
<p class="t_txt">키바나는 시각화 기술로 히스토그램, 막대그래프, 파이차트를 표현하는 것부터 위치데이터, 시계열 분석, 그래프관계 탐색 등을 지원한다.</p>

<div class="t_ptype btn_img_zoom">
<div class="edtitor_img_uio"><span class="img_wrap2"><img title="" src="http://the-r.kr/wp-content/uploads/2017/03/06.png" alt="" data-src="http://ncc.phinf.naver.net/20161207_272/1481072674586A5H1e_PNG/b06.png" /></span>
<p class="cap">데이터를 시각화하고 <span class="word_dic en">Elastic</span> <span class="word_dic en">Stack</span>의 탐색을 지원하는 키바나 화면 예제 &lt;출처: 엘라스틱 홈페이지&gt;</p>

</div>
</div>
<p class="t_txt">엘라스틱은 현재 5개국어를 지원하고 있는데, 한국어도 포함돼 있다. 그만큼 한국시장 진출을 활발히 하고 있음을 엿볼 수 있다. 2015년 6월에는 한국인 디벨로퍼 어드보케이트(기술전도사)를 따로 채용해 커뮤니티 지원을 활발히 하고 있다. 2016년에는 고객 행사도 대규모로 열어 입지를 넓히고 있다. 한국에서는 삼성, <span class="word_dic en">SK</span>텔레콤, <span class="word_dic en">GS</span>샵, <span class="word_dic en">NHN</span>엔터테인먼트 등이 엘라스틱 고객사다.</p>
<p class="t_txt">최근 엘라스틱이 강조하는 기술이 바로 ‘프리러트(<span class="word_dic en">Prelert</span>)’다. 프리러트는 2016년 엘라스틱에 인수된 기업으로, 이상 데이터 및 외부 공격을 감지하는 기능을 제공한다. 머신러닝(기계학습)을 결합한 것이 특징이며, <span class="word_dic en">ELK</span> 스택에 최적화된 기술을 지원하고 있다.</p>

<dl class="na_reference">
 	<dt>참고링크</dt>
 	<dd>
<ul>
 	<li><a href="http://www.bloter.net/archives/234528" target="_blank">엘라스틱 “오픈소스 검색기술로 기업혁신 돕고파”</a>(블로터, 이지현)</li>
 	<li><a href="http://www.elastic.co/kr/" target="_blank">엘락스틱 홈페이지</a></li>
</ul>
</dd>
</dl>