<script lang="ts">
	import Heart from '#lib/assets/Heart.svelte';
	import X from '#lib/assets/X.svelte';

	import Input from './Input.svelte';
	import Button from './Button.svelte';
	import { onMount } from 'svelte';
	interface PopupProps {
		isOpen?: boolean;
	}

	let { isOpen = false }: PopupProps = $props();

	let coordinateTitle = $state('');
	let xCoordinate = $state('');
	let yCoordinate = $state('');
	let zCoordinate = $state('');

	let coordinates = $state(JSON.parse(localStorage.getItem('coordinates') ?? '[]'));

	let saveCoordinates = () => {
		let inputCoordinates = $state({
			title: coordinateTitle,
			coordinates: { x: xCoordinate, y: yCoordinate, z: zCoordinate },
			id: coordinates.length
		});

		coordinates.push(inputCoordinates);

		localStorage.setItem('coordinates', JSON.stringify(coordinates));

		window.location.reload();
	};

	onMount(() => {
		document.addEventListener('keydown', (e) => {
			if (e.key == 'Escape') {
				isOpen = false;
			}

			if (e.key == 'Enter') {
				saveCoordinates();
			}
		});

		//if user has no saved coordinates just add them to ls so the error doesnt accur

		if (!coordinates) {
			localStorage.setItem('coordinates', '');
		}
	});
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

		<Input placeholder="Title e.g. House" bind:value={coordinateTitle} />

		<div class="popup-input-wrapper">
			<Input class="coordinate-input" bind:value={xCoordinate} placeholder="X" />
			<Input class="coordinate-input" bind:value={yCoordinate} placeholder="Y" />
			<Input class="coordinate-input" bind:value={zCoordinate} placeholder="Z" />
		</div>

		<Button
			class="save-coordinates-button flex-center-row"
			smallGlow
			onclick={() => {
				saveCoordinates();
			}}><Heart /> Save</Button
		>
	</div>
{/if}

<style>
	:global(.popup-close) {
		position: absolute;
		inset: var(--spacing-lg) var(--spacing-lg) auto auto;
		z-index: 99999;
		cursor: pointer;
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
