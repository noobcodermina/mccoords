<script lang="ts">
	import Heart from '#lib/assets/Heart.svelte';
	import X from '#lib/assets/X.svelte';

	import Input from './Input.svelte';
	import Button from './Button.svelte';
	interface PopupProps {
		isOpen?: boolean;
	}

	let { isOpen = false }: PopupProps = $props();
</script>

<Button
	smallGlow
	onclick={() => {
		isOpen = true;
	}}><Heart /> Add coordinates</Button
>

{#if isOpen}
	<div class="popup-wrapper flex-center-column">
		<X
			class="popup-close"
			onclick={() => {
				isOpen = false;
			}}
		/>
		<h2>Save coordinates</h2>

		<Input placeholder="Title e.g. House" />

		<div class="popup-input-wrapper">
			<Input class="coordinate-input" placeholder="X" />
			<Input class="coordinate-input" placeholder="Y" />
			<Input class="coordinate-input" placeholder="Z" />
		</div>

		<Button class="save-coordinates-button flex-center-row" smallGlow><Heart /> Save</Button>
	</div>
{/if}

<style>
	:global(.popup-close) {
		position: absolute;
		inset: var(--spacing-lg) var(--spacing-lg) auto auto;
		z-index: 99999;
	}
	.popup-wrapper {
		position: absolute;
		inset: var(--spacing-none);
		background: var(--black-bg);
		h2 {
			color: var(--text-primary);
			margin-bottom: var(--spacing-lg);
		}
		.popup-input-wrapper {
			margin-top: var(--spacing-lg);
			:global(.coordinate-input) {
				width: 81px !important;
			}
		}
		:global(.save-coordinates-button) {
			width: 250px;
			margin-top: var(--spacing-lg);
		}
	}
</style>
