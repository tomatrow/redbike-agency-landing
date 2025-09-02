<script lang="ts">
	import { FlyText } from "$lib"
</script>

<section>
	<p>
		<FlyText
			text="Every project possesses a unique purpose and beauty, requiring a customized collection of strategic and creative services to deliver results."
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

		@media only screen and (min-width: 720px) {
			padding: 10rem 1rem;
		}
	}

	p {
		max-width: 1000px;
		line-height: 1.5;
		font-size: 2rem;
		font-family: "Space Grotesk";

		@media only screen and (min-width: 720px) {
			font-size: 2.5rem;
			line-height: 1;
		}
	}
</style>
