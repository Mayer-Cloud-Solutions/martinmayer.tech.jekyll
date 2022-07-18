---
layout: page
menu: false
date: '2022-06-30 01:53:59'
title: Portfolio
permalink: /portfolio/
description: Martin Mayer | Technical Leader | Portfolio
---

# Portfolio

<!--<div class="component">
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
	</div>
	<img src="https://res.cloudinary.com/martinmayer-tech/image/upload/v1657837062/right_dqqp0w.svg" alt="go to next slide" onclick="goRight()">
</div>-->
<section id="grid" class="row flex-grid">
        {% for initiative in site.initiatives%}
            <article class="box-item">
                <!--<span class="category">
                    <a href="{{ site.baseurl }}/{{ site.categories_folder | default: 'category' }}/{{ post.category }}">
                        <span>{{ post.category }}</span>
                    </a>
                </span>-->
                <div class="box-body">
                    <a class="cover" href="{{ initiative.url | prepend: site.baseurl }}">
                        {% include loader.html %}
                        {% if initiative.optimized_image %}
                            <img src="/assets/img/placeholder.png" width="100%" data-url="{{ initiative.optimized_image }}" class="preload">
                            <noscript>
                                <img src="{{ initiative.optimized_image }}" width="100%">
                            </noscript>
                        {% elsif initiative.image %}
                            <img src="/assets/img/placeholder.png" width="100%" data-url="{{ initiative.image }}" class="preload">
                            <noscript>
                                <img src="{{ initiative.image }}" width="100%">
                            </noscript>
                        {% else %}
                            <img src="/assets/img/placeholder.png" width="100%" data-url="/assets/img/off.jpg" class="preload">
                            <noscript>
                                <img src="/assets/img/off.jpg" width="100%">
                            </noscript>
                        {% endif %}
                        {% include new-post-tag.html date=initiative.date %}
                        {% include read-icon.html %}
                    </a>
                    <div class="box-info">
                        <time datetime="{{ initiative.date | date_to_xmlschema }}" class="date">
                            {% include date.html date=initiative.date %}
                        </time>
                        <a class="post-link" href="{{ initiative.url | prepend: site.baseurl }}">
                            <h2 class="post-title">
                                {{ initiative.title }}
                            </h2>
                        </a>
                        <a class="post-link" href="{{ initiative.url | prepend: site.baseurl }}">
                            <p class="description">{{ initiative.description }}</p>
                        </a>
                        <!--<div class="tags">
                            {% for tag in initiative.tags %}
                                {% if tag != "" %}
                                    <a href="{{ site.baseurl}}/tags/#{{tag | slugify }}">#{{ tag }}</a>
                                {% endif %}
                            {% endfor %}
                        </div>-->
                    </div>
                </div>
            </article>
        {% endfor %}
    </section>


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