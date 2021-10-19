<script>
	import NavBar from "./_components/NavBar.svelte";
</script>

<NavBar />

<main>
	<slot />
</main>

<style>
	main {
		height: calc(100vh - 80px);
		width: 100%;
	}
</style>
