<script lang="ts">
	import WelcomeBookmark from '#lib/assets/WelcomeBookmark.svelte';
	import WelcomePin from '#lib/assets/WelcomePin.svelte';
	import WelcomeCheck from '#lib/assets/WelcomeCheck.svelte';
	import WelcomePlay from '#lib/assets/WelcomePlay.svelte';
	import Button from '#lib/components/Button.svelte';
	import WelcomeSquare from '#lib/components/WelcomeSquare.svelte';

	import shared from '#lib/shared.svelte.ts';
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
		<p>just a dashboard</p>
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
	}
</style>
