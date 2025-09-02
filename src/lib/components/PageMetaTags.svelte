<script lang="ts">
	import { MetaTags } from "svelte-meta-tags"

	const siteName = "Red Bike Agency"
	const siteDescription =
		"Red Bike Agency offers expert digital branding, web design, and development services to help brands grow and connect with their audience. Build momentum today."

	let {
		canonical,
		title = siteName,
		description = siteDescription
	}: {
		canonical: string
		title?: string
		description?: string
	} = $props()

	const ogImageUrl = `https://redbike.agency/og-image.png`
	const ogImageAlt = siteName
</script>

<MetaTags
	{title}
	titleTemplate="%s | Enhance Your Brand – Get Started"
	{description}
	{canonical}
	openGraph={{
		url: canonical,
		title,
		description,
		siteName,
		images: [
			{
				url: ogImageUrl,
				width: 1000,
				height: 600,
				alt: ogImageAlt
			}
		]
	}}
	twitter={{
		creator: "@handle",
		site: "@site",
		cardType: "summary_large_image",
		title,
		description,
		image: ogImageUrl,
		imageAlt: ogImageAlt
	}}
/>

<svelte:head>
	<link
		rel="icon"
		type="image/x-icon"
		media="(prefers-color-scheme: light)"
		href="/light-favicon.ico"
	/>
	<link
		rel="icon"
		type="image/x-icon"
		media="(prefers-color-scheme: dark)"
		href="/dark-favicon.ico"
	/>
</svelte:head>
