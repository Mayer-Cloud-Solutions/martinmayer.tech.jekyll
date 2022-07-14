---
layout: page
menu: false
date: '2022-06-30 01:53:59'
title: Portfolio
permalink: /portfolio/
description: Martin Mayer | Technical Leader | Portfolio
---

<img class="img-rounded" src="/assets/img/uploads/martinmayer.jpg" alt="Martin Mayer" width="200">

# Portfolio

<p>Portfolio</p>

<p>This carousel is created with HTML and CSS only.</p>

<div class="component">
	<img src="left.svg" alt="go to previous slide" onclick="goLeft()"> 
	<div class="carousel">
		<div class="slide" id="slide1"></div>
		<div class="slide" id="slide2"></div>
		<div class="slide" id="slide3"></div>
	</div>
	<img src="right.svg" alt="go to next slide" onclick="goRight()">
</div>
<script>
	function goRight() {
		document.querySelector(".carousel").scrollLeft += 240;
	}

	function goLeft() {
		document.querySelector(".carousel").scrollLeft -= 240;
	 }

</script>