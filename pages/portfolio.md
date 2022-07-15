---
layout: page
menu: false
date: '2022-06-30 01:53:59'
title: Portfolio
permalink: /portfolio/
description: Martin Mayer | Technical Leader | Portfolio
---

# Portfolio

<div class="component">
	<img src="https://res.cloudinary.com/martinmayer-tech/image/upload/v1657837062/left_qqqq8i.svg" alt="go to previous slide" onclick="goLeft()"> 
	<div class="carousel">
		{% for initiative in site.initiatives %}
		<div class="slide" id="{{ initiative.reference }}" style="background: linear-gradient( rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7) ), url('{{ initiative.bg_img }}'); background-repeat: no-repeat; background-attachment: fixed; background-size: cover;">
		  <h2 class="carouseltext">{{ initiative.title }}</h2>
		  <h3 class="carouseltext">{{ initiative.subtitle }}</h3>
		  <h4 class="carouseltext">{{ initiative.business }} - {{ initiative.init_date }}</h4>
		  <p class="carouseltext">{{ initiative.content | markdownify }}</p>
		</div>
		{% endfor %}
	
		<!--<div class="slide" id="slide1"></div>
		<div class="slide" id="slide2"></div>
		<div class="slide" id="slide3"></div>-->
	</div>
	<img src="https://res.cloudinary.com/martinmayer-tech/image/upload/v1657837062/right_dqqp0w.svg" alt="go to next slide" onclick="goRight()">
</div>
<script>
	const slideMargin = 0;
		
	function goRight() {
	
		if (document.querySelector(".carousel").scrollLeft + document.querySelector(".carousel").clientWidth + (slideMargin * 2) >= document.querySelector(".carousel").scrollWidth + slideMargin) {
			document.querySelector(".carousel").scrollLeft = slideMargin;
		}
		else {
			document.querySelector(".carousel").scrollLeft += document.querySelector(".carousel").clientWidth + (slideMargin * 2);
		}
	}

	function goLeft() {
		if (document.querySelector(".carousel").scrollLeft <= slideMargin) {
			document.querySelector(".carousel").scrollLeft = document.querySelector(".carousel").scrollWidth + slideMargin - document.querySelector(".carousel").clientWidth + (slideMargin * 2);
		}
		else {
			document.querySelector(".carousel").scrollLeft -= document.querySelector(".carousel").clientWidth + (slideMargin * 2);
		}		
	 }

</script>