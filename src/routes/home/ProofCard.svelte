<script lang="ts">
	import { Collapsible } from "melt/components"
	import { slide, fade } from "svelte/transition"
	import { cubicOut } from "svelte/easing"
	import ToggleIcon from "./ToggleIcon.svelte"
	import { RevealContainer } from "$lib"

	let {
		src,
		name,
		items
	}: {
		src: string
		name: string
		items: string[]
	} = $props()
</script>

<article>
	<RevealContainer x={400}>
		<img {src} alt={name} />
	</RevealContainer>
	<Collapsible>
		{#snippet children(collapsible)}
			<button {...collapsible.trigger}>
				<span>{name}</span>

				<ToggleIcon open={collapsible.open} />
			</button>

			{#if collapsible.open}
				<div {...collapsible.content} transition:slide>
					<ul>
						{#each items as item, index (item)}
							<li transition:fade|global={{ delay: index * 150 + 100, easing: cubicOut }}>
								<p>{item}</p>
							</li>
						{/each}
					</ul>
				</div>
			{/if}
		{/snippet}
	</Collapsible>
</article>

<style>
	article {
		display: flex;
		flex-direction: column;
		padding-top: 1rem;
		padding-bottom: 1rem;
	}

	img {
		aspect-ratio: 0.8;
		min-height: 0;
		object-fit: cover;
	}

	button {
		width: 100%;
		display: flex;
		justify-content: space-between;
		color: var(--accent);
		border-left: none;
		border-right: none;
		border-color: var(--text);
		margin-top: 1rem;
		color: var(--text);
		padding: 0.5rem 0;
		font-weight: 500;

		background: none;
		&:hover {
			background: none;
		}
	}

	ul {
		padding-left: 1rem;
	}
</style>
