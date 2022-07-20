---
layout: main
permalink: /portfolio/
description: Martin Mayer | Technical Leader | Portfolio
---
# Portfolio
<main class="home no-padding" role="main">
	<div class="backgrounded">
		<section id="grid" class="row flex-grid">
			<h1>Portfolio</h1>
			{% for initiative in site.initiatives %}
				<article class="box-item">
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
							{% include read-icon.html %}
						</a>
						<div class="box-info">
							<time datetime="{{ initiative.date | date_to_xmlschema }}" class="date">
								{% include date.html date=initiative.init_date %}
							</time>
							<a class="post-link" href="{{ initiative.url | prepend: site.baseurl }}">
								<h2 class="post-title">
									{{ initiative.title }}
								</h2>
							</a>
							<a class="post-link" href="{{ initiative.url | prepend: site.baseurl }}">
								<p class="description">{{ initiative.description }}</p>
							</a>
						</div>
					</div>
				</article>
			{% endfor %}
		</section>
	</div>
</main>

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