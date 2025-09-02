<script lang="ts">
	import { fly } from "svelte/transition"
	import { cubicInOut } from "svelte/easing"
	import type { Snippet } from "svelte"
	import { useIntersectionObserver } from "runed"

	let {
		axis = "x",
		children,
		class: clazz
	}: {
		axis: "x" | "y" | "-x" | "-y"
		class?: string
		children?: Snippet
	} = $props()

	let target = $state<HTMLElement>()
	let showCover = $state(true)
	let didEndOutro = $state(false)
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
	let clientWidth = $state(0)
	let clientHeight = $state(0)

	const flyProps = $derived.by(() => {
		switch (axis) {
			case "x":
				return { x: -clientWidth }
			case "-x":
				return { x: clientWidth }
			case "y":
				return { y: -clientHeight }
			case "-y":
				return { y: clientHeight }
		}
	})
</script>

<div class={["reveal-container", clazz]} class:enabled={!didEndOutro}>
	{@render children?.()}
	{#if showCover}
		<div
			class="cover"
			bind:this={target}
			bind:clientWidth
			bind:clientHeight
			out:fly|global={{
				opacity: 1,
				easing: cubicInOut,
				duration: 500,
				...flyProps
			}}
			onoutroendcapture={() => (didEndOutro = true)}
		></div>
	{/if}
</div>

<style>
	.reveal-container {
		&.enabled {
			position: relative;
			overflow: clip;
		}

		.cover {
			background: var(--bg);
			position: absolute;
			inset: 0;
		}
	}
</style>
