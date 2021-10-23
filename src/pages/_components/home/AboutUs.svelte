<script>
	import { url } from "@roxi/routify";
</script>

<section>
	<div class="content-wrapper">
		<article>
			<p class="pretext">About Us</p>
			<h1 class="title"><span>Our </span>Story</h1>
			<p class="preview-text">
				Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod
				tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim
				veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea
				commodo consequat. Duis aute irure dolor in reprehenderit in voluptate
				velit esse cillum dolore eu fugiat nulla pariatur.
			</p>
			<a href="./about" use:$url class="learn-more">Learn More</a>
		</article>

		<div class="img-section">
			<div class="img-wrapper">
				<!-- <img src="./imgs/farmer-img.jpg" alt="Farmer" /> -->
			</div>
		</div>
	</div>
</section>

<style lang="scss">
	section {
		border: var(--border);
	}
</style>
