<script lang="ts">
	import { Instagram } from "@lucide/svelte"
</script>

<footer>
	<a class="company" href="/"><h3>Red Bike Agency</h3></a>
	<a href="mailto:hello@redbike.agency">hello@redbike.agency</a>
	<a class="social" href="https://www.instagram.com/redbike.agency" target="_blank">
		<Instagram />
	</a>
</footer>

<style>
	footer {
		background: black;
		display: flex;
		flex-direction: column;
		gap: 1rem;
		justify-content: center;
		align-items: center;
		padding: 2rem;

		.company {
			padding: 1rem;
			color: white;
		}

		a {
			&:hover {
				color: white;
			}
		}
	}
</style>
