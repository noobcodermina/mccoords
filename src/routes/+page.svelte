<script lang="ts">
	import WelcomeBookmark from '#lib/assets/WelcomeBookmark.svelte';
	import WelcomePin from '#lib/assets/WelcomePin.svelte';
	import WelcomeCheck from '#lib/assets/WelcomeCheck.svelte';

	import Header from '#lib/components/Header.svelte';

	import Button from '#lib/components/Button.svelte';
</script>

<div class="welcome-wrapper flex-center-column">
	<div class="flex-center-row">
		<div class="pin-rectangle">
			<WelcomePin />
		</div>
		<div class="save-rectangle">
			<WelcomeBookmark />
		</div>
		<div class="check-rectangle">
			<WelcomeCheck />
		</div>
	</div>
	<h1>
		Coordinates <span class="as">saving</span> <br /> made <span class="colored-text">simple</span>
	</h1>
	<p>Super simple way to save your Minecraft coordinates</p>

	<Button></Button>
</div>

<style>
	.welcome-wrapper {
		width: 100%;
		height: 100dvh;
		gap: calc(var(--spacing-lg) * 2);
		h1 {
			text-align: center;
			font-size: 3rem;
			line-height: 2.8rem;

			.colored-text {
				color: #adff2f;
				font-style: italic;
				font-weight: bold;
			}
		}
		.save-rectangle {
			width: 80px;
			height: 80px;
			transform: rotate(45deg);
			background-color: #adff2f;
			border-radius: 2rem;
			animation: pulse 3s infinite ease-in;
			box-shadow: 0 0 20px 2px yellowgreen;
			padding: 1.2rem;
		}
		.pin-rectangle {
			width: 80px;
			height: 80px;
			background-color: #4169e1;
			border-radius: 2rem;
			animation: pulse 3s infinite ease-in;
			box-shadow: 0 0 20px 2px #4169e1;
			padding: 1.2rem;
		}

		.check-rectangle {
			width: 80px;
			height: 80px;
			background-color: orange;
			border-radius: 2rem;
			box-shadow: 0 0 20px 2px orange;
			padding: 1.2rem;
			animation: pulse 3s infinite ease-in;
		}
	}
</style>
