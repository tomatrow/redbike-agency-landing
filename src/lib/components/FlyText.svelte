<script lang="ts">
	import { fly } from "svelte/transition"
	import { cubicOut } from "svelte/easing"

	let {
		text,
		delayGap = 10,
		duration = 700,
		y = 60
	}: { y?: number; text: string; delayGap?: number; duration?: number } = $props()

	const tokens = text.split(/(\s+)/)
</script>

<span class="words" aria-live="polite">
	{#each tokens as token, i (i)}
		{#if token.trim() === ""}
			{@html token}
		{:else}
			<span class="word" in:fly|global={{ y, duration, delay: i * delayGap, easing: cubicOut }}
				>{token}</span
			>
		{/if}
	{/each}
</span>

<style>
	.words {
		display: inline; /* keep normal inline flow */
		white-space: pre-wrap; /* preserve multiple spaces and wrap */
		line-height: 1.3;
	}

	.word {
		display: inline-block; /* prevents layout shift when transforming */
		will-change: transform, opacity;
		transform-origin: center;
		/* optional niceties */
		backface-visibility: hidden;
	}

	/* small accessibility / reduced-motion support */
	@media (prefers-reduced-motion: reduce) {
		.word {
			transition: none !important;
		}
	}
</style>
