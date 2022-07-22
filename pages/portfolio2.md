---
layout: main
permalink: /portfolio2/
title: Portfolio2
description: Martin Mayer | Technical Leader | Portfolio
---
# Portfolio

{% if site.paginate %}
    {% assign initiatives = paginator.initiatives | where_exp:"initiative","initiative.is_generated != true" %}
{% else %}
    {% assign initiatives = site.initiatives | where_exp:"initiative","initiative.is_generated != true" %}
{% endif %}

{% if site.show_hero and paginator == nil or paginator.page == 1 %}
    {% assign offset = 1 %}
{% else %}
    {% assign offset = 0 %}
{% endif %}

<main class="home {% if site.show_hero and paginator == nil or paginator.page == 1 %}no-padding{% endif %}" role="main">
    {% if site.show_hero and paginator == nil or paginator.page == 1 %}
        <!-- Hero -->
        {% assign featured = initiatives.first %}
        <section class="hero" style="background-image: url({{ featured.image }})">
            <div class="pixels"></div>
            <div class="gradient"></div>
            <div class="content">
                <h1 class="title">{{ featured.title }}</h1>
                <p class="description">{{ featured.subtitle }}</p>
                <div class="buttons">
                    <a href="{{ featured.url | prepend: site.baseurl }}" role="button" class="button">
                        <svg><use xlink:href="#icon-read"></use></svg>
                        <span>{{ site.translations.button.read_now | default: "Read Now" }}</span>
                    </a>
                </div>
            </div>
        </section>
    {% endif %}
    <!-- Initiatives -->
    <section id="grid" class="row flex-grid">
        {% for initiative in initiatives offset: offset %}
            <article class="box-item">
                <span class="category">
                    <a href="{{ site.baseurl }}/{{ site.categories_folder | default: 'category' }}/{{ initiative.category }}">
                        <span>{{ initiative.category }}</span>
                    </a>
                </span>
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
						<time datetime="{{ initiative.init_date | date_to_xmlschema }}" class="date">
							{{ initiative.init_date | date: "%B, %Y" }}
						</time>
                        <a class="post-link" href="{{ initiative.url | prepend: site.baseurl }}">
                            <h2 class="post-title">
                                {{ initiative.title }}
                            </h2>
                        </a>
                        <a class="post-link" href="{{ initiative.url | prepend: site.baseurl }}">
                            <p class="description">{{ initiative.description }}</p>
                        </a>
                        <div class="tags">
                            {% for tag in initiative.tags %}
                                {% if tag != "" %}
                                    <a href="{{ site.baseurl}}/tags/#{{tag | slugify }}">#{{ tag }}</a>
                                {% endif %}
                            {% endfor %}
                        </div>
                    </div>
                </div>
            </article>
        {% endfor %}
    </section>
    <!-- Pagination -->
    {% if site.paginate %}
        {% include pagination-home.html %}
    {% endif %}
</main>

{% assign social_urls = '' %}
{% if site.github_username %}
    {% assign social_urls = social_urls | append: '"https://github.com/' | append: site.github_username | append: '",' %}
{% endif %}
{% if site.facebook_username %}
    {% assign social_urls = social_urls | append: '"https://www.facebook.com/' | append: site.facebook_username | append: '",' %}
{% endif %}
{% if site.twitter_username %}
    {% assign social_urls = social_urls | append: '"https://twitter.com/' | append: site.twitter_username | append: '",' %}
{% endif %}
{% if site.medium_username %}
    {% assign social_urls = social_urls | append: '"https://medium.com/@' | append: site.medium_username | append: '",' %}
{% endif %}
{% if site.instagram_username %}
    {% assign social_urls = social_urls | append: '"https://www.instagram.com/' | append: site.instagram_username | append: '",' %}
{% endif %}
{% if site.linkedin_username %}
    {% assign social_urls = social_urls | append: '"https://www.linkedin.com/in/' | append: site.linkedin_username | append: '",' %}
{% endif %}
<script>

	document.addEventListener("DOMContentLoaded", function(){
		const element = document.getElementById("portfolio");
		if ( typeof element !== null && element !== 'undefined' ) {
			element.remove();
		}
	});
	
	document.querySelector("portfolio").addEventListener('load', function(){
		const element = document.getElementById("portfolio");
		if ( typeof element !== null && element !== 'undefined' ) {
			element.remove();
		}
	});

</script>
<script type="application/ld+json">
{
  "@context": "http://schema.org",
  "@type": "WebPage",
  "mainEntity": {
    "@type": "Blog",
    "name": "{{ site.name }}",
    "headline": "{{ site.title }}",
    "description": "{{ site.description }}",
    "url": "{{ site.url }}{{site.baseurl}}/",
    "inLanguage": "{{ site.language }}",
    "isFamilyFriendly": "true",
    "creator": {
        "@type": "Organization",
        "name": "{{ site.name }}",
        "url": "{{ site.url }}{{site.baseurl}}/",
        "sameAs": [
            {{ social_urls | split: "," | join: "," }}
        ]
    },
    "mainEntity": {
        "@type": "ItemList",
        "itemListElement": [
        {% assign limit = 8 %}
        {% for initiative in initiative limit: limit %}
            {% assign author = site.authors | where: "name", initiative.author | first %}
            {
                "@type": "BlogPosting",
                "name": "{{ initiative.title }}",
                "headline": "{{ initiative.subtitle }}",
                "description": "{{ initiative.description }}",
                "image": "{{ initiative.image }}",
                "url": "{{ initiative.url | prepend: site.baseurl | prepend: site.url }}",
                "inLanguage": "{{ site.language }}",
                "dateCreated": "{{ initiative.date | date: '%Y-%m-%d/' }}",
                "datePublished": "{{ initiative.date | date: '%Y-%m-%d/' }}",
                "dateModified": "{{ initiative.date | date: '%Y-%m-%d/' }}",
                "author": {
                    "@type": "Person",
                    "name": "{{ author.display_name }}",
                    "url": "{{ author.url | prepend: site.baseurl | prepend: site.url }}"
                },
                "publisher": {
                    "@type": "Organization",
                    "name": "{{ site.name }}",
                    "url": "{{ site.url }}{{site.baseurl}}/",
                    "logo": {
                        "@type": "ImageObject",
                        "url": "{{ site.url }}{{site.baseurl}}/assets/img/blog-image.png",
                        "width": "600",
                        "height": "315"
                    }
                },
                "mainEntityOfPage": "True",
                "genre": "{{ initiative.category | capitalize }}",
		        "articleSection": "{{ initiative.category | capitalize }}",
                "keywords": [{{ initiative.tags | join: '","' | append: '"' | prepend: '"' }}]
            }{% if forloop.last == false  %},{% endif %}
        {% endfor %}
        ]
    }
  }
}
</script>
