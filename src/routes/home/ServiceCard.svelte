<script lang="ts">
	let { name, items }: { name: string; items: string[] } = $props()
</script>

<article>
	<h5>
		<div class="background"></div>
		<span>{name}</span>
	</h5>
	<ul>
		{#each items as item (item)}
			<li>{item}</li>
		{/each}
	</ul>
</article>

<style>
	article {
		padding: 1rem 1rem;
	}

	ul {
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
		padding-left: 1rem;
	}

	h5 {
		position: relative;
		text-align: center;
		display: inline-flex;
		padding: 1rem;
		overflow: visible;
		text-align: center;
		justify-content: center;
		align-items: center;
		margin-left: -1rem;
	}

	.background {
		overflow: visible;
		position: absolute;
		inset: 0;
		background-color: var(--accent);
		mask: url("assets/highlight3.svg");
		mask-size: contain;
		mask-repeat: no-repeat;
		mask-position: 50% 50%;
		mask-origin: 50% 50%;
		z-index: -1;
	}
</style>
