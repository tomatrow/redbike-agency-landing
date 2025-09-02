<script lang="ts">
	import { FlyText } from "$lib"
</script>

<section>
	<p>
		<FlyText
			text="Our multidisciplinary approach enables us to create complete and compelling brand experiences."
		/>
	</p>
</section>

<style>
	section {
		background: var(--accent);
		color: var(--bg);
		overflow: hidden;
		display: flex;
		justify-content: center;
		padding: 4rem 1rem;

		@media (min-width: 720px) {
			padding: 8rem 1rem;
		}
	}

	p {
		max-width: 1000px;
		line-height: 1.5;
		font-size: 2rem;
		font-family: "Space Grotesk";

		@media (min-width: 720px) {
			font-size: 2.5rem;
		}
	}
</style>
