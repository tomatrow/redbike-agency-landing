<script lang="ts">
	import { Collapsible } from "melt/components"
	import { slide, fade } from "svelte/transition"
	import { cubicOut } from "svelte/easing"
	import ToggleIcon from "./ToggleIcon.svelte"

	let {
		name,
		items
	}: {
		name: string
		items: string[]
	} = $props()
</script>

<article>
	<img src="/images/readfriends.webp" alt={name} />
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
	}

	img {
		aspect-ratio: 1;
		min-height: 0;
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
