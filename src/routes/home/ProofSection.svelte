<script lang="ts">
	import { Collapsible } from "melt/components"
	import { slide } from "svelte/transition"
	import { Cross } from "@lucide/svelte"

	let name = "Hi-Fi Friends"
	let items = ["Brand Identity", "Brand Logo", "Brand Strategy", "Web Design/Development"]
</script>

<article>
	<img src="/images/readfriends.webp" alt={name} />
	<Collapsible>
		{#snippet children(collapsible)}
			<button {...collapsible.trigger}>
				<span>{name}</span>
				<Cross />
			</button>

			{#if collapsible.open}
				<div {...collapsible.content} transition:slide>
					<ul>
						{#each items as item (item)}
							<li><p>{item}</p></li>
						{/each}
					</ul>
				</div>
			{/if}
		{/snippet}
	</Collapsible>
</article>

<style>
	button {
		width: 100%;
		display: flex;
		justify-content: space-between;
	}
</style>
