<script>
	import Github from '#lib/assets/Github.svelte';
	import Logo from './Logo.svelte';

	import shared from '#lib/shared.svelte.ts';
</script>

<header class="flex-between-row">
	<Logo />
	<nav class="flex-center-row">
		<p
			role="presentation"
			onclick={() => {
				shared.isDashboardVisible = true;
			}}
		>
			Dashboard
		</p>
		<Github
			class="github-svg"
			onclick={() => {
				window.open('https://github.com/noobcodermina/mccoords', '_blank');
			}}
		/>
	</nav>
</header>

<style>
	header {
		position: fixed;
		top: 0;
		width: min(100%, 1200px);
		padding: calc(var(--spacing-lg) * 2);
		nav {
			gap: calc(var(--spacing-lg) * 2);
		}
		p {
			cursor: pointer;
			color: var(--text-primary);
			font-weight: var(--text-bold);
		}
		:global(.github-svg) {
			cursor: pointer;
		}
	}
</style>
