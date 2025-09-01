<script lang="ts">
	import { Instagram, Menu, X } from "@lucide/svelte"
	import { MediaQuery } from "svelte/reactivity"
	import { fly } from "svelte/transition"
	import { cubicInOut } from "svelte/easing"
	import { beforeNavigate } from "$app/navigation"

	let showMenu = $state(false)
	let isMobile = new MediaQuery("max-width: 720px")

	beforeNavigate(() => {
		showMenu = false
	})

	$effect(() => {
		if (isMobile && showMenu) {
			document.body.classList.add("no-scroll")
		} else {
			document.body.classList.remove("no-scroll")
		}
	})
</script>

<header>
	<a href="/"><img src="/images/logo.webp" alt="red bike" /> </a>
	<button class="mobile icon-only" onclick={() => (showMenu = true)}><Menu /></button>
	<nav class="desktop">
		<a href="/">home</a>
		<a href="/about">about us</a>
		<a class="social" href="https://www.instagram.com/redbike.agency" target="_blank">
			<Instagram />
		</a>
	</nav>

	{#if showMenu && isMobile}
		<nav class="mobile" transition:fly={{ y: 10, duration: 200, easing: cubicInOut, opacity: 0 }}>
			<button class="icon-only" onclick={() => (showMenu = false)}><X /></button>
			<ul>
				<li><a href="/">home</a></li>
				<li><a href="/about">about us</a></li>
			</ul>
			<a class="social" href="https://www.instagram.com/redbike.agency" target="_blank">
				<Instagram />
			</a>
		</nav>
	{/if}
</header>

<style>
	:global {
		.no-scroll {
			overflow: hidden;
		}
	}

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

	nav.desktop {
		display: none;
		gap: 1rem;
		--accent: #fff;
		--accent-hover: #fff;

		a.social {
			margin-left: 2rem;
			width: 1rem;
			transform: translate(0, 1px);
		}
	}

	nav.mobile {
		--accent: black;
		--accent-hover: black;

		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		height: 100vh;
		display: flex;
		flex-direction: column;
		gap: 1rem;
		padding: 1rem;
		background: var(--bg);
		justify-content: space-between;

		.social {
			justify-self: flex-end;
		}

		button {
			color: var(--accent);
			align-self: flex-end;
			justify-self: flex-start;
		}

		ul {
			display: flex;
			flex-direction: column;
			gap: 1.5rem;
		}
	}

	button.icon-only {
		background: none;
		border: none;

		&:hover {
			background: none;
		}
	}

	@media only screen and (min-width: 720px) {
		nav.desktop {
			display: flex;
		}

		button.mobile {
			display: none;
		}
	}
</style>
