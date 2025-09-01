<script lang="ts">
	import ProofCard from "./ProofCard.svelte"
</script>

<section>
	<h2>Paths We've Paved</h2>

	<div class="section-content">
		<div class="proof-grid first">
			<ProofCard
				src="/images/readfriends.webp"
				name="Hi-Fi Friends"
				items={["Brand Identity", "Brand Logo", "Brand Strategy", "Web Design/Development"]}
			/>
			<ProofCard
				src="/images/sign.webp"
				name="Refuge Bible Fellowship"
				items={["Brand Identity", "Brand Logo", "Brand Strategy"]}
			/>
		</div>

		<div class="proof-grid second">
			<ProofCard
				src="/images/radius.webp"
				name="Radius Coffee App"
				items={[
					"Brand Identity",
					"Brand Logo",
					"Brand Strategy",
					"Web Design/Development",
					"iOS Development"
				]}
			/>
			<ProofCard
				src="/images/foodme.webp"
				name="Food me App"
				items={["Brand Identity", "Brand Logo", "Brand Strategy"]}
			/>
		</div>
	</div>
</section>

<style>
	section {
		padding: 1rem;
		max-width: 1200px;
		margin: auto;
	}

	.section-content {
		display: flex;
		flex-direction: column;

		@media only screen and (min-width: 720px) {
			flex-direction: row;
			gap: 4rem;
		}
	}

	.proof-grid {
		display: flex;
		flex-direction: column;

		@media only screen and (min-width: 720px) {
			flex: 1;
		}

		&.second {
			padding-top: 10rem;
		}
	}
</style>
