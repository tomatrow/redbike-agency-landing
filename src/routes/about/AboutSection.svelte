<script lang="ts">
	import { RevealContainer } from "$lib"
</script>

<section>
	<RevealContainer class="image-content" axis="x">
		<img
			src="images/board.webp"
			alt="man in a dim room pointing at whiteboard covered in stickynotes"
		/>
	</RevealContainer>

	<div class="text-content">
		<h5>
			Our human-centric approach to branding leads us to explore how people engage and react to your
			brand through unique assets, memories, stories, emotions, and experiences.
		</h5>
		<p>
			We partner with brands ready to build with purpose and get noticed. Our process is an
			intentional blend of thoughtful brand strategy, compelling storytelling, and expert design to
			guide your brand's journey.
		</p>
		<p>
			Ultimately, we believe the key components to setting your brand in motion are the roadmap that
			guides the ride, the gears that build momentum, and the riders you're creating the journey
			for.
		</p>
	</div>
</section>

<style>
	section {
		padding: 2rem 1rem;
		display: flex;
		flex-direction: column;
		max-width: 1200px;
		margin: auto;

		@media (min-width: 720px) {
			flex-direction: row;
			gap: 4rem;

			:global(.image-content),
			.text-content {
				flex: 1;
			}
		}
	}

	section :global(.image-content) {
		img {
			max-height: 14rem;
			width: 100%;
			object-fit: cover;

			@media (min-width: 720px) {
				max-height: 100%;
				height: 100%;
			}
		}
	}

	.text-content {
		h5 {
			padding: 3rem 0;

			@media (min-width: 720px) {
				padding: 0rem 0rem 1rem 0rem;
				font-size: 2rem;
			}
		}

		p {
			margin-top: 2rem;

			@media (min-width: 720px) {
				margin-top: 1rem;
			}
		}
	}
</style>
