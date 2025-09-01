<script lang="ts">
	import { fly } from "svelte/transition"
	import { cubicInOut } from "svelte/easing"
	import type { Snippet } from "svelte"
	import { useIntersectionObserver } from "runed"

	let {
		x,
		y,
		children
	}: {
		x?: number
		y?: number
		children?: Snippet
	} = $props()

	let target = $state<HTMLElement>()
	let showCover = $state(true)
	let observer = useIntersectionObserver(
		() => target,
		(entries) => {
			const ratio = entries[0]?.intersectionRatio ?? 0
			if (ratio < 0.3) return

			showCover = false
			observer.stop()
		},
		{ threshold: 1 / 3 }
	)
</script>

<div class="reveal-container">
	{@render children?.()}
	{#if showCover}
		<div
			class="cover"
			bind:this={target}
			out:fly|global={{
				opacity: 1,
				easing: cubicInOut,
				duration: 500,
				x,
				y
			}}
		></div>
	{/if}
</div>

<style>
	.reveal-container {
		position: relative;
		overflow: hidden;

		.cover {
			background: #fff;
			position: absolute;
			inset: 0;
			z-index: 1;
			width: 100%;
			height: 100%;
		}
	}
</style>
