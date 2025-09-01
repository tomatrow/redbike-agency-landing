<script lang="ts">
	import { RevealContainer } from "$lib"
</script>

<section>
	<h2>About Us</h2>

	<div class="content">
		<div class="description">
			<p>
				At Red Bike, we are passionate about guiding brands through their digital journey. Our team
				brings over two decades of combined experience to every project, crafting powerful online
				presences. We work with intentionality to build the right foundation for your brand's
				growth, whether you need a quick tune-up or a full custom build. Our goal is to help you
				build momentum and connect with your ideal audience, so you can truly set your brand in
				motion.
			</p>
		</div>

		<div class="team-image">
			<RevealContainer axis="y">
				<img src="/images/team.webp" alt="aj and nic in a field dressed like hobbits" />
			</RevealContainer>
			<p>We are a pair of lifelong friends for over 20 Years!</p>
		</div>
	</div>
</section>

<style>
	section {
		padding: 4rem 2rem;
		max-width: 1200px;
		margin: auto;

		.content {
			display: flex;
			flex-direction: column;
			gap: 1rem;

			@media (min-width: 720px) {
				flex-direction: row;

				.description,
				.team-image {
					flex: 1;
				}
			}
		}
	}

	h2 {
		margin-bottom: 4rem;
	}

	.description {
		@media only screen and (min-width: 720px) {
			display: flex;
			justify-content: center;
			align-items: center;

			p {
				max-width: 400px;
				line-height: 1.5;
			}
		}
	}

	.team-image {
		position: relative;
		display: flex;
		justify-content: center;

		:global(.reveal-container) {
			img {
				object-fit: cover;
				object-position: 50% 50%;
				aspect-ratio: 1;
				min-height: 0;
				width: 100%;

				@media (min-width: 720px) {
					aspect-ratio: 0.5;
					max-width: 400px;
				}
			}
		}

		p {
			position: absolute;
			background: var(--accent-bg);
			bottom: 0;
			left: 50%;

			padding: 1rem;
			margin-right: 10%;
			margin-bottom: -2rem;
			max-width: 16rem;
			line-height: 1.2;
		}
	}
</style>
