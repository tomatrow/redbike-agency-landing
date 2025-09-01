<script lang="ts">
	import { fly } from "svelte/transition"
	import { cubicOut } from "svelte/easing"
	import { useIntersectionObserver } from "runed"

	let {
		text,
		delayGap = 10,
		duration = 700,
		y = 60
	}: { y?: number; text: string; delayGap?: number; duration?: number } = $props()

	let container = $state<HTMLElement>()
	let showText = $state(false)
	let oberver = useIntersectionObserver(
		() => container,
		(entries) => {
			const ratio = entries[0]?.intersectionRatio ?? 0
			if (ratio < 1 / 2) return

			showText = true
			oberver.stop()
		}
	)

	let tokens = $derived(text.split(/(\s+)/))
</script>

<span bind:this={container} class="words" aria-live="polite">
	{#if showText}
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
	{/if}
</span>

<style>
	.word {
		display: inline-block; /* prevents layout shift when transforming */
	}
</style>
