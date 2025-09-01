<script lang="ts">
	import favicon from "$lib/assets/favicon.svg"
	import Header from "./Header.svelte"
	import Footer from "./Footer.svelte"
	import "../global.css"

	let { children } = $props()
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<Header />

<main>
	{@render children?.()}
</main>

<Footer />
