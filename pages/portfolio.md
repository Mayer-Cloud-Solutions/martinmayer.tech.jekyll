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

<p>This carousel is created with HTML and CSS only.</p>

<div class="component">
	<img src="https://res.cloudinary.com/martinmayer-tech/image/upload/v1657837062/left_qqqq8i.svg" alt="go to previous slide" onclick="goLeft()"> 
	<div class="carousel">
		<div class="slide" id="slide1"></div>
		<div class="slide" id="slide2"></div>
		<div class="slide" id="slide3"></div>
	</div>
	<img src="https://res.cloudinary.com/martinmayer-tech/image/upload/v1657837062/right_dqqp0w.svg" alt="go to next slide" onclick="goRight()">
</div>
<script>
	function goRight() {
		if (document.querySelector(".carousel").scrollLeft + 240 >= document.querySelector(".carousel").scrollWidth + 20) {
			document.querySelector(".carousel").scrollLeft = 20;
		}
		else {
			document.querySelector(".carousel").scrollLeft += 240;
		}
	}

	function goLeft() {
		if (document.querySelector(".carousel").scrollLeft <= 20) {
			document.querySelector(".carousel").scrollLeft = document.querySelector(".carousel").scrollWidth + 20 - 240;
		}
		else {
			document.querySelector(".carousel").scrollLeft -= 240;
		}		
	 }

</script>