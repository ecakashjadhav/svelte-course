<script>
	export let size = 'small';
	export let shadow = false;
	export let bgColor = 'inherit';
	export let textColor = 'inherit';
	// export let disabled = false; {...$$restProps} use to get passed value from App Button


	let isLeftHovered=false;
</script>

<button on:click
	style:--buttonBgColor={bgColor}
	style:--buttonTextColor={textColor}
	class:size-lg={size === 'large'}
	class:size-sm={size === 'small'}
	class:has-left={$$slots.leftContent}
	class:shadow
	{...$$restProps}
 >
	{#if $$slots.leftContent}
		<!-- svelte-ignore a11y-no-static-element-interactions -->
		<div
			class="left-content"
			on:mouseenter={() => (isLeftHovered = true)}
			on:mouseleave={() => (isLeftHovered = false)}
		>
			<slot {isLeftHovered} name="leftContent" />
		</div>
	{/if}
	<slot>Fallback</slot>
</button>

<style lang="scss">
	button {
		display: flex;
		align-items: center;
		border: none;
		background-color: var(--buttonTextColor);
		color: var(--buttonColor);
		font-weight: bold;
		border-radius: 5px;
		cursor: pointer;
		.left-content {
			margin: 10px;
		}
		&:hover {
			background-image: linear-gradient(rgba(0, 0, 0, 0.4), 0, 0);
		}
		&.size-lg {
			padding: 20px 25px;
			font-size: 20px;
		}
		&.size-sm {
			padding: 15px 20px;
		}
		&.shadow {
			box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
		}
		&:disabled {
			cursor: not-allowed;
			opacity: 0.5;
		}
	}
</style>
