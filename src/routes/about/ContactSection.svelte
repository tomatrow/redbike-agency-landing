<section id="contact">
	<header>
		<h2>Let’s Work Together</h2>
		<p>We collaborate with ambitious brands. Let’s go the distance together.</p>
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
			align-items: center;
			gap: 2rem;

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
