<script lang="ts">
	import ServiceCard from "./ServiceCard.svelte"
</script>

<section>
	<header>
		<h2>What We Do</h2>

		<p>
			We plan, design, strategize, create, make, produce, and curate brand experiences for humans.
		</p>
	</header>

	<div class="services">
		<ServiceCard
			name="Strategy"
			items={[
				"Consulting",
				"Strategy",
				"Innovation",
				"Management",
				"Research & Analysis",
				"Brand Portfolio & Architecture"
			]}
		/>
		<ServiceCard
			name="Creative"
			items={[
				"Brand Identity",
				"Brand Guidelines",
				"Art Direction",
				"Naming",
				"Packaging & Print",
				"Illustration"
			]}
		/>
		<ServiceCard
			name="Digital"
			items={["Web Design", "User Interface Design", "User Experience Design"]}
		/>
		<ServiceCard
			name="Development"
			items={[
				"iOS App Development",
				"Web Development",
				"Front End development",
				"Back End development"
			]}
		/>
	</div>
</section>

<style>
	section {
		padding: 5rem 1rem;
		display: flex;
		flex-direction: column;
		margin: auto;
		gap: 1rem;

		@media (min-width: 720px) {
			flex-direction: row;
			max-width: 1000px;

			header,
			.services {
				flex: 1;
			}

			.services {
				display: grid;
				grid-template-columns: 1fr 1fr;
				/* gap: 1rem; */
			}
		}
	}

	h2 {
		padding: 3rem 0;
	}

	p {
		padding: 2rem 0;
		max-width: 20rem;
	}
</style>
