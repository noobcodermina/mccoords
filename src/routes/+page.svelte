<script lang="ts">
	import WelcomeBookmark from '#lib/assets/WelcomeBookmark.svelte';
	import WelcomePin from '#lib/assets/WelcomePin.svelte';
	import WelcomeCheck from '#lib/assets/WelcomeCheck.svelte';
	import WelcomePlay from '#lib/assets/WelcomePlay.svelte';
	import Button from '#lib/components/Button.svelte';
	import WelcomeSquare from '#lib/components/WelcomeSquare.svelte';

	import Trash from '#lib/assets/Trash.svelte';

	import Input from '#lib/components/Input.svelte';
	import Popup from '#lib/components/Popup.svelte';
	import shared from '#lib/shared.svelte.ts';
	import { onMount } from 'svelte';

	//some search stuff that works somehow idfk know how lmao
	let userInput = $state('');

	interface Coordinate {
		title: string;
		coordinates: {
			x: string;
			y: string;
			z: string;
		};
		id: string;
	}

	let coordinates: Coordinate[] = $state([]);

	onMount(() => {
		coordinates = JSON.parse(localStorage.getItem('coordinates') ?? '[]');
	});

	let filtered = $derived(
		coordinates.filter((i) => i.title.toLowerCase().includes(userInput.toLowerCase()))
	);
</script>

{#if shared.isDashboardVisible === false}
	<div class="welcome-wrapper flex-center-column">
		<div class="flex-center-row">
			<WelcomeSquare variant="blue">
				<WelcomePin />
			</WelcomeSquare>
			<WelcomeSquare variant="green">
				<WelcomeBookmark />
			</WelcomeSquare>
			<WelcomeSquare variant="orange">
				<WelcomeCheck />
			</WelcomeSquare>
		</div>
		<h1>
			Coordinates <span class="as">saving</span> <br /> made
			<span class="colored-welcome-text">simple</span>
		</h1>
		<p>Super simple way to save your Minecraft coordinates</p>

		<Button
			onclick={() => {
				shared.isDashboardVisible = true;
			}}>Continue to dashboard <WelcomePlay /></Button
		>
	</div>
{:else}
	<div class="dashboard-wrapper">
		<h2>My coordinates</h2>
		<div class="flex-center-row dashboard-ib-wrapper">
			<Input placeholder="Search" bind:value={userInput} />
			<Popup />
		</div>
		<div class="coordinates-wrapper">
			{#each filtered as mock, i (i)}
				<div class="flex-center-row coordinate-wrapper">
					<div class="edit-delete-wrapper flex-center-column">
						<Trash
							onclick={() => {
								coordinates = coordinates.filter((item) => item.id !== mock.id);
								localStorage.setItem('coordinates', JSON.stringify(coordinates));
							}}
						/>
					</div>
					<div class="flex-start-column">
						<p class="coordinate-title">
							{mock.title}
						</p>
						<p class="coordinate-coordinates">
							{mock.coordinates.x}
							{mock.coordinates.y}
							{mock.coordinates.z}
						</p>
					</div>
				</div>
			{/each}
			{#if filtered.length == 0}
				<p>one big nothing :p</p>
			{/if}
		</div>
	</div>
{/if}

<style>
	.welcome-wrapper {
		width: 100%;
		height: calc(100dvh - calc(var(--spacing-lg) * 5));
		gap: calc(var(--spacing-lg) * 2);
		h1 {
			text-align: center;
			font-size: calc(var(--text-lg) * 2);
			line-height: 2.8rem;

			.colored-welcome-text {
				color: var(--green);
				font-weight: var(--bold);
				font-style: italic;
			}
		}
		p {
			text-align: center;
		}
	}

	.dashboard-wrapper {
		padding: calc(var(--spacing-lg) * 2);
		margin-top: calc(var(--spacing-lg) * 3);

		h2 {
			color: var(--text-primary);
		}
		.coordinates-wrapper {
			margin-top: calc(var(--spacing-lg) * 3);
			div {
				padding: var(--spacing-md) 0;
				.coordinate-title {
					color: var(--text-primary);
					font-weight: var(--text-bold);
				}
				.coordinate-coordinates {
					margin-top: var(--spacing-sm);
				}
			}
		}
		.dashboard-ib-wrapper {
			margin-top: calc(var(--spacing-lg) * 3);
			justify-content: flex-start;
			gap: var(--spacing-lg);

			@media (max-width: 600px) {
				flex-direction: column;
				align-items: flex-start;
			}
		}
	}

	.edit-delete-wrapper {
		width: fit-content;
	}

	.coordinate-wrapper {
		width: fit-content;
		gap: var(--spacing-lg);
	}
</style>
