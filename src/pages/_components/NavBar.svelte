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
	$: toggleFreeze = navOpen && pageWidth < 769;
	$: if (pageWidth > 768) navOpen = false;
	const toggleNav = () => (navOpen = !navOpen);
</script>

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

	<ul class:open={navOpen}>
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
		// border: var(--border);
		width: Max(300px, 100%);
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
			width: 30px;
			height: 4px;
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
		position: absolute;
		z-index: 2;
		padding: 0;
		background: white;
		top: 100%;
		right: 0;
		height: calc(100vh - 80px);
		display: block;
		width: 300px;
		transition: transform 0.25s ease-in-out;
		transform: translateX(100%);
		box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);

		li {
			margin: 0;
			display: block;

			a {
				padding: 30px;
				display: block;

				&.active {
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

	// ul {
	// 	height: 100%;
	// 	list-style: none;
	// 	display: flex;

	// 	li {
	// 		display: flex;
	// 		align-items: center;
	// 		margin: 0 25px;
	// 	}

	// 	a {
	// 		text-transform: uppercase;
	// 		font-weight: var(--semi-bold);
	// 		font-size: var(--normal);

	// 		&.active {
	// 			color: var(--green);
	// 			font-weight: var(--bold);
	// 		}
	// 	}
	// }

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
