<section id="contact">
	<header>
		<h2>Let’s Work Together</h2>
		<p>
			Red Bike Agency operates under the belief that businesses can perform more of a role within
			our community than just providing services for profit. We want to use our skills, services,
			and resources to support ideas, movements, and organizations that exist to do some good.
			Sometimes this looks like us donating our resources or time, and other times it could be a
			reduced fee or donation. Either way, it’s about doing our bit for better.
		</p>
		<a href="mailto:hello@redbike.agency">hello@redbike.agency</a>
	</header>
	<div class="calendy-container">
		<!-- Calendly inline widget begin -->
		<div class="calendly-inline-widget">
			<iframe
				src="https://calendly.com/redbikeagency"
				width="100%"
				height="100%"
				frameborder="0"
				title="calendly"
			>
			</iframe>
		</div>
		<!-- Calendly inline widget end -->
	</div>
</section>

<style>
	section {
		padding: 4rem 1rem;
		display: flex;
		flex-direction: column;
		gap: 4rem;
		max-width: 1200px;
		margin: auto;

		@media (min-width: 720px) {
			flex-direction: row;
			gap: 2rem;
			align-items: center;

			header,
			.calendy-container {
				flex: 1;
			}
		}
	}

	header {
		display: flex;
		flex-direction: column;
		gap: 2rem;

		p {
			@media (min-width: 720px) {
				max-width: 24rem;
			}
		}
	}

	.calendy-container {
		.calendly-inline-widget {
			min-width: 320px;
			height: 700px;
		}
	}
</style>
