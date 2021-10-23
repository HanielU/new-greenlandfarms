<script>
	import { url, isActive } from "@roxi/routify";

	const links = [
		{ path: "./index", name: "Home" },
		{ path: "./services", name: "Services" },
		{ path: "./about", name: "About" },
		{ path: "./contact", name: "Contact Us" },
	];

	let navOpen = false;
	let pageWidth = 0;
	$: toggleFreeze = navOpen && pageWidth < 768;
	$: if (pageWidth > 768) navOpen = false;
	const toggleNav = () => (navOpen = !navOpen);
</script>

<svelte:window bind:innerWidth={pageWidth} />
<div class="freeze-bg" class:open={toggleFreeze} on:click={toggleNav} />

<nav class:open={navOpen}>
	<div class="logo">
		<a href="/index" use:$url>
			<img src="/imgs/logo.jpg" alt="Greenland Farms Logo" />
		</a>
	</div>

	<button class="menu-btn" on:click={toggleNav} class:open={navOpen}>
		<div class="menu-btn__burger" />
	</button>

	<ul class:open={navOpen} style={`--page-width: ${pageWidth}px`}>
		{#each links as link}
			<li>
				<a
					href={link.path}
					use:$url
					class:active={$isActive(link.path)}
					on:click={toggleNav}
				>
					{link.name}
				</a>
			</li>
		{/each}
	</ul>
</nav>

<style lang="scss">
	nav {
		width: Max(280px, 100%);
		height: 80px;
		position: sticky;
		top: 0;
		z-index: 3;
		background: #fff;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 0 15px;
		box-shadow: 0px 23px 38px 0px rgba(0, 0, 0, 0.1);
	}

	.logo {
		height: 80%;
		width: 50px;

		img {
			height: 100%;
		}
	}

	.menu-btn {
		height: 100%;
		padding: 0 20px;
		background: transparent;
		cursor: pointer;

		&__burger {
			width: 27px;
			height: 3.5px;
			background: var(--font-color-primary);
			transition: all 0.25s ease-in-out;
			position: relative;
			border-radius: 5px;

			&::before,
			&::after {
				content: "";
				position: absolute;
				left: 0;
				width: inherit;
				height: inherit;
				background: var(--font-color-primary);
				transition: all 0.25s ease-in-out;
				border-radius: 5px;
			}
			&::before {
				transform: translateY(-8px);
			}
			&::after {
				transform: translateY(8px);
			}
		}

		&.open &__burger {
			background: transparent;
			transition: all 0.025s ease-in-out;
			&::before {
				transform: rotate(45deg);
			}
			&::after {
				transform: rotate(-45deg);
			}
		}
	}

	ul {
		width: 300px;
		height: calc(100vh - 80px);
		background: white;
		position: absolute;
		z-index: 1;
		top: 100%;
		right: 0;
		transition: transform 0.25s ease-in-out;
		transform: translateX(100%);
		box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);

		li {
			a {
				text-transform: uppercase;
				font-weight: var(--semi-bold);
				font-size: var(--normal);
				padding: 30px;
				display: block;

				&.active {
					color: var(--green);
					background: #f0f0f0;
				}
			}

			&:hover {
				background: #f0f0f0;
			}
		}

		&.open {
			transform: translateX(0);
		}
	}

	@media screen and (min-width: 480px) {
		nav {
			padding: 0 25px;
		}

		.menu-btn__burger {
			width: 30px;
			height: 4px;
		}
	}

	@media screen and (min-width: 767px) {
		nav {
			padding: 0 50px;
		}

		.menu-btn {
			display: none;
		}

		ul {
			position: initial;
			transform: none;
			box-shadow: none;
			height: 100%;
			width: auto;
			display: flex;

			li {
				display: flex;
				align-items: center;
				margin: 0 25px;

				a {
					padding: 0;
					display: inline;

					&.active {
						background: white;
					}
				}

				&:hover {
					background: white;
				}
			}
		}
	}

	@media screen and (max-width: 300px) {
		.logo {
			height: 65%;
		}

		.menu-btn__burger {
			width: 25px;
			height: 3px;
		}

		ul {
			width: var(--page-width);
		}
	}

	.freeze-bg {
		background: rgba(0, 0, 0, 0.5);
		width: 100%;
		height: 100vh;
		position: fixed;
		top: 0;
		left: 0;
		z-index: -1;
		overflow: hidden;
		opacity: 0;
		transition: all 0.25s ease-in-out;

		&.open {
			opacity: 1;
			z-index: 2;
		}
	}
</style>
