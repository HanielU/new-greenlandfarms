<section>
	<div class="intro-text-wrapper">
		<h1 class="title">Greenland Farms</h1>
		<h3 class="subtitle">Farms and Management</h3>
	</div>
</section>

<style>
	section {
		height: min(80%, 80vh);
		width: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
		margin-bottom: 50px;
		background-image: url(/imgs/hero-bg.jpg);
		background-position: center;
		background-repeat: no-repeat;
		background-size: cover;
	}

	.intro-text-wrapper {
		font-family: var(--font-secondary);
		color: #fff;
	}

	.title {
		font-size: var(--huge);
		font-weight: var(--bold);
	}

	.subtitle {
		font-size: var(--large);
		font-weight: var(--semibold);
	}

	@media screen and (min-width: 768px) {
		section {
			padding-left: 100px;
			justify-content: flex-start;
		}
	}
</style>
