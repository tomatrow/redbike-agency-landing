<script lang="ts">
	let { open }: { open?: boolean } = $props()
</script>

<div class="icon {open ? 'open' : 'closed'}">
	<span class="line horizontal"></span>
	<span class="line vertical"></span>
</div>

<style>
	.icon {
		position: relative;
		width: 20px;
		height: 20px;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.line {
		position: absolute;
		background-color: currentColor;
		transition: transform 0.3s cubic-bezier(0.215, 0.61, 0.355, 1);
	}

	.horizontal {
		width: 16px;
		height: 1px;
	}

	.vertical {
		width: 1px;
		height: 16px;
	}

	.icon.open .vertical {
		transform: rotate(90deg);
	}

	.icon.closed .vertical {
		transform: rotate(0deg);
	}
</style>
