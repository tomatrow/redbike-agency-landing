<script lang="ts">
	import { FlyText } from "$lib"
</script>

<section>
	<h2>
		<FlyText text="Set Your Brand in Motion" />
	</h2>
	<a class="button" href="#contact">Let's get to work</a>
</section>

<style>
	section {
		background: var(--accent-bg);
		overflow: hidden;
		padding: 8rem 0rem;
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 2rem;

		@media only screen and (min-width: 720px) {
			gap: 6rem;
		}
	}

	h2 {
		font-size: 2rem;
		margin: 0;
		text-align: center;
		line-height: 1;
		color: white;

		@media only screen and (min-width: 720px) {
			font-size: 4rem;
		}
	}
</style>
