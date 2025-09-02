<script lang="ts">
	import type { HTMLButtonAttributes } from "svelte/elements"

	let {
		open,
		...rest
	}: {
		open?: boolean
	} & HTMLButtonAttributes = $props()
</script>

<button class:open {...rest}>
	<div class="line top"></div>
	<div class="line bottom"></div>
</button>

<style>
	button {
		position: relative;
		aspect-ratio: 1;
		min-height: 0;
		width: 100%;
		height: 100%;
	}

	.line {
		position: absolute;
		background: var(--menu-color, currentColor);
		height: 1px;
		width: 80%;
		transition: all 200ms ease-out;

		&.top {
			left: 50%;
			top: 40%;
			transform: translate(-50%, -50%);
		}

		&.bottom {
			left: 50%;
			top: 60%;
			transform: translate(-50%, -50%);
		}
	}
	
	button.open {
		.line.top {
			top: 50%;
			transform: translate(-50%, -50%) rotate(225deg) ;
		}
		
		.line.bottom {
			top: 50%;
			transform: translate(-50%, -50%) rotate(-225deg)  ;
		}
	}
</style>
