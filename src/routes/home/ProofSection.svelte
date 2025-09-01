<script lang="ts">
	import { Collapsible } from "melt/components"
	import { slide, fade } from "svelte/transition"
	import { cubicOut } from "svelte/easing"
	import { Plus } from "@lucide/svelte"

	let name = "Hi-Fi Friends"
	let items = ["Brand Identity", "Brand Logo", "Brand Strategy", "Web Design/Development"]
</script>

<section>
	<article>
		<img src="/images/readfriends.webp" alt={name} />
		<Collapsible>
			{#snippet children(collapsible)}
				<button {...collapsible.trigger}>
					<span>{name}</span>
					<Plus class="icon {collapsible.open ? 'open' : 'closed'}" />
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
</section>

<style>
	section {
		padding: 1rem;
	}

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

		background: none;
		&:hover {
			background: none;
		}
	}

	ul {
		padding-left: 1rem;
	}

	:global(.icon) {
		transition: transform 0.3s cubic-bezier(0.215, 0.61, 0.355, 1);
	}

	:global(.icon.closed) {
		transform: rotate(0deg);
	}

	:global(.icon.open) {
		transform: rotate(45deg);
	}
</style>
