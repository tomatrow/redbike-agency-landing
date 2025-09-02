<script lang="ts">
	import { PageMetaTags } from "$lib"
	import Header from "./Header.svelte"
	import Footer from "./Footer.svelte"
	import "../global.css"
	import { page } from "$app/state"

	let { children } = $props()
</script>

<PageMetaTags
	canonical={`https://redbike.agency${page.url.pathname === "/" ? "" : page.url.pathname}`}
/>

<Header />

<main>
	{@render children?.()}
</main>

<Footer />
