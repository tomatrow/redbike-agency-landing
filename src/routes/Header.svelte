<script lang="ts">
	import { Instagram } from '@lucide/svelte';
</script>

<header>
	<a href="/">
		<img src="/images/logo.webp" alt="red bike" />
	</a>
	<nav>
		<a href="/">home</a>
		<a href="/about">about us</a>
		<a class="social" href="https://www.instagram.com/redbike.agency" target="_blank">
			<Instagram />
		</a>
	</nav>
</header>

<style>
	header {
		position: sticky;
		top: 0;
		left: 0;
		right: 0;
		background: var(--accent-bg);
		display: flex;
		padding: 1rem;
		align-items: center;
		justify-content: space-between;
	}

	img {
		width: 235px;
	}

	nav {
		display: flex;
		gap: 1rem;

		a.social {
			margin-left: 2rem;
			width: 1rem;
			transform: translate(0, 1px);
		}
	}
</style>
