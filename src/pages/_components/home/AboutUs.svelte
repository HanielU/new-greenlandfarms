<script>
	import { url } from "@roxi/routify";
</script>

<section class="content-wrapper">
	<div class="content">
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
	article {
		margin-bottom: 30px;

		h1 {
			font-size: var(--very-large);

			span {
				color: var(--green);
			}
		}
	}

	.preview-text {
		margin: 20px 0 20px 0;
	}

	a {
		padding: 10px 20px;
		display: block;
		width: fit-content;
		background: var(--green);
		color: #fff;
	}

	.img-section {
		height: 300px;
		width: 300px;
		margin: auto;
	}

	.img-wrapper {
		height: 100%;
		width: 100%;
		border-radius: 50%;
		overflow: hidden;
		background-image: url(/imgs/farmer-img.jpg);
		background-position: center;
		background-repeat: no-repeat;
		background-size: cover;
	}

	@media screen and (min-width: 768px) {
	}
</style>
