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
			<!--  eslint-disable-next-line svelte/no-at-html-tags -->
			{@html token}
		{:else}
			<span class="word" in:fly|global={{ y, duration, delay: i * delayGap, easing: cubicOut }}
				>{token}</span
			>
		{/if}
	{/each}
</span>

<style>
	.word {
		display: inline-block; /* prevents layout shift when transforming */
	}
</style>
