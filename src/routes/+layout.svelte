<script>
	import Header from '$lib/Header.svelte';
	import Footer from '$lib/Footer.svelte';
</script>

<div class="screen">
	<Header />
	<slot />
	<Footer />
</div>

<style>
	.screen {
		display: flex;
		position: relative;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		width: 100vw;
		height: 100vh;
	}
</style>
