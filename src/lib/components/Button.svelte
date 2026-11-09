<script>
	import WelcomePlay from '#lib/assets/WelcomePlay.svelte';
</script>

<button class="flex-center-row">Get Started <WelcomePlay /></button>

<style>
	button {
		background-color: var(--white-bg);
		padding: var(--spacing-lg) calc(var(--spacing-lg) * 2);
		border: 1px solid black;
		border-radius: 1rem;
		box-shadow: 0 0 20px 1px grey;
		font-weight: bold;
		cursor: pointer;
		gap: var(--spacing-lg);
	}
</style>
