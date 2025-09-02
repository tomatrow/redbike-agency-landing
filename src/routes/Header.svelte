<script lang="ts">
	import { Instagram } from "@lucide/svelte"
	import { MediaQuery } from "svelte/reactivity"
	import { fly } from "svelte/transition"
	import { cubicInOut, cubicOut } from "svelte/easing"
	import { beforeNavigate } from "$app/navigation"
	import { page } from "$app/state"
	import MenuIcon from "./MenuIcon.svelte"

	let showMenu = $state(false)
	let isMobile = new MediaQuery("max-width: 720px")

	const floatUp = { y: 10, duration: 600, easing: cubicOut }

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
	<a class="desktop-logo" in:fly|global={floatUp} href="/"
		><img src="/images/logo.webp" alt="red bike" /></a
	>
	<nav in:fly|global={floatUp} class="desktop-nav">
		<a href="/" aria-current={page.url.pathname === "/"}>home</a>
		<a href="/about" aria-current={page.url.pathname === "/about"}>about us</a>
		<a class="social" href="https://www.instagram.com/redbike.agency" target="_blank">
			<Instagram />
		</a>
	</nav>

	<a class="mobile-logo" in:fly|global={floatUp} href="/"
		><img src="/images/logo-mobile.webp" alt="red bike" /></a
	>
	<div class="mobile-menu-button icon-only" in:fly|global={floatUp}>
		<MenuIcon open={showMenu} onclick={() => (showMenu = !showMenu)} --menu-color={
			showMenu
				? "black"
				: "white"
			}  />
	</div>
	{#if showMenu && isMobile}
		<nav
			class="mobile-nav"
			transition:fly={{ y: 10, duration: 200, easing: cubicInOut, opacity: 0 }}
		>
			<ul>
				<li><a href="/" aria-current={page.url.pathname === "/"}>home</a></li>
				<li><a href="/about" aria-current={page.url.pathname === "/about"}>about us</a></li>
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
	
	a[aria-current = true] {
		border-bottom: 1px solid currentColor;
	}

	header {
		position: sticky;
		top: 0;
		left: 0;
		right: 0;
		background: var(--accent);
		display: flex;
		padding: 1rem;
		align-items: center;
		justify-content: space-between;
		z-index: 1000;
	}

	.mobile-logo {
		max-width: 100px;
		margin: auto;

		@media (min-width: 720px) {
			display: none;
		}
	}

	.mobile-menu-button {
		position: absolute;
		top: 50%;
		right: 1rem;
		transform: translateY(-50%);
		width: 2rem;
		z-index: 1000;

		@media (min-width: 720px) {
			display: none;
		}
	}

	.mobile-nav {
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
		justify-content: center;

		.social {
			position: absolute;
			left: 1rem;
			bottom: 1rem;
		}
 
		ul {
			display: flex;
			flex-direction: column;
			gap: 1.5rem;
		}
	}

	.desktop-logo {
		display: none;

		@media (min-width: 720px) {
			display: unset;
		}

		img {
			width: 235px;
		}
	}

	.desktop-nav {
		display: none;
		gap: 1rem;
		--accent: #fff;
		--accent-hover: #fff;

		@media (min-width: 720px) {
			display: flex;
		}

		a.social {
			margin-left: 2rem;
			width: 1rem;
			transform: translate(0, 1px);
		}
	}
</style>
