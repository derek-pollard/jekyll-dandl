---
id: 1209
title: Home
date: 2009-02-08T11:10:13+00:00
author: Derek
layout: home
guid: http://www.derekandlindsay.co.uk/?page_id=1209
banner-heading:
  - 'Hello &amp; Welcome'
banner-content:
  - 'We are Derek &amp; Lindsay and we live in Ipswich, England.  Thank you for visiting us as we share some of our favourite things.  From tales about the beautiful critters who have made up our family over the years, short stories and other things we love.'
banner-colour:
  - '#5c2c63'
template: homepage
---

<div id="areas" class="fourwide">
  <div class="area">
    <a href="/pets/bunnies/"><img src="/images/homepage/bunnies.jpg" alt="Bunnies" /></a>
    
    <h2>
      <a href="/pets/bunnies/">Bunnies</a>
    </h2>
  </div>
  
  <div class="area">
    <a href="/pets/rats/"><img src="/images/homepage/ratties.jpg" alt="Ratties" /></a> 
    
    <h2>
      <a href="/pets/rats/">Ratties</a>
    </h2>
  </div>
  
  <div class="area">
    <a href="/pets/cats/"><img src="/images/homepage/cats.jpg" alt="Cats" /></a>
    
    <h2>
      <a href="/pets/cats/">Cats</a>
    </h2>
  </div>
  
  <div class="area last">
    <a href="/pets/degus/"><img src="/images/homepage/home_degu.jpg" alt="Degus" /></a>
    
    <h2>
      <a href="/pets/degus/">Degus</a>
    </h2>
  </div>
  
  <div class="area">
    <a href="/pets/gerbils/"><img src="/images/homepage/gerbils.jpg" alt="Gerbils" /></a>
    
    <h2>
      <a href="/pets/gerbils/">Gerbils</a>
    </h2>
  </div>
  
  <div class="area">
    <a href="/pets/guinea-pigs/"><img src="/images/homepage/guineapigs.jpg" alt="Guinea Pigs" /></a>
    
    <h2>
      <a href="/pets/guinea-pigs/">Guinea Pigs</a>
    </h2>
  </div>
  
  <div class="area">
    <a href="/short-stories/"><img src="/images/homepage/stories.jpg" alt="Stories" /></a>
    
    <h2>
      <a href="/short-stories/">Stories</a>
    </h2>
  </div>
  
  <div class="area last">
    <a href="/trailers/"><img src="/images/homepage/sillytrailers.jpg" alt="Silly Trailers" /></a>
    
    <h2>
      <a href="/trailers/">Trailers</a>
    </h2>
  </div>
</div>

<div id="updates" class="tintbg">
	<h2>What's new with Derek and Lindsay</h2>

{% for post in site.posts %}
	{% for categoryInstance in site.pages %}
		{% assign categorySlug = categoryInstance.name | replace: '.md', '' %}
		{% if categorySlug == post.category-slug %}
			{% assign categoryPage = categoryInstance %}
			{% break %}
		{% endif %}
	{% endfor %}

	{% capture anchorurl %}
	{{ categoryPage.url }}#{% include postidtoanchor.html path=post.id %}
	{% endcapture %}
	
	{% assign post_image = post.content | match_regex: '<img .*?src="/([^"]+)"' %}
	{% if post_image == nil %}
		{% assign post_image = "images/DandLsquare.png" %}
	{% endif %}

	{% assign remainder = forloop.index | modulo: 3 %}	
	
	<div class="update{% if remainder == 0 %} last{% endif %}">
		<a href="{{ anchorurl }}">
			{% thumbnail post_image 70x70 %}
		</a>
		<div class="details">
		<h3><a href="{{ anchorurl }}">{{ post.title }}</a></h3>
		<p>{{ post.date | date: "%-d %B %Y" }}</p>
		</div>
	</div>

{% endfor %}

</div>
<div class="clearer"></div>
