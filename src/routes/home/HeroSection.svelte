<script lang="ts">
	import { FlyText, RevealContainer } from "$lib"
</script>

<section>
	<div class="container">
		<RevealContainer axis="y" --bg="var(--accent)" class="image flyer">
			<img src="images/flyer.webp" alt="flyer with pleasant people" />
		</RevealContainer>

		<div class="title">
			<h2><FlyText text="Set Your Brand in Motion" /></h2>
			<RevealContainer axis="y" --bg="var(--accent)">
				<a class="button" href="#contact">Let's get to work</a>
			</RevealContainer>
		</div>

		<RevealContainer axis="y" --bg="var(--accent)" class="image bar">
			<img src="images/bar.webp" alt="" />
		</RevealContainer>
	</div>
</section>

<style>
	section {
		background: var(--accent);

		.container {
			max-width: 1000px;
			padding: 1rem;
			margin: auto;
			overflow: hidden;
			display: flex;
			flex-direction: column;
			align-items: center;
			gap: 2rem;

			@media (min-width: 720px) {
				gap: 0.5rem;
				flex-direction: row;
				justify-content: space-between;
				min-height: 700px;
			}
		}
	}

	section :global .image {
		min-height: 0;

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
		}

		&.flyer {
			aspect-ratio: 1;
			align-self: flex-start;
			max-width: 33%;

			@media (min-width: 720px) {
				width: 100%;
				max-width: 33%;
			}
		}

		&.bar {
			aspect-ratio: 0.8;
			align-self: flex-end;
			max-width: 33%;

			@media (min-width: 720px) {
				width: 100%;
				max-width: 25%;
			}
		}
	}

	.title {
		text-align: center;

		h2 {
			font-size: 2rem;
			margin: 0;
			line-height: 1;
			color: white;

			@media (min-width: 720px) {
				font-size: 3rem;
			}
		}

		a.button {
			margin-top: 1rem;
			text-transform: uppercase;
			--button: var(--accent);
			--button-bg: var(--accent-bg);
		}
	}
</style>
