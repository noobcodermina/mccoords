<script lang="ts">
	import type { Snippet } from 'svelte';

	interface WSprops {
		children: Snippet;

		variant: 'blue' | 'green' | 'orange';
	}

	let { children, variant }: WSprops = $props();
</script>

<div
	class="welcome-square"
	class:blue-square={variant === 'blue'}
	class:green-square={variant === 'green'}
	class:orange-square={variant === 'orange'}
>
	{@render children()}
</div>

<style>
	.welcome-square {
		width: 80px;
		aspect-ratio: 1;
		border-radius: calc(var(--radius-lg) + 0.5rem);
		padding: calc(var(--spacing-lg) + 0.2rem);
	}

	.blue-square {
		background: royalblue;
		box-shadow: var(--glow-blue);
	}
	.green-square {
		background: greenyellow;
		box-shadow: var(--glow-green);
		transform: rotate(45deg);

		animation: squareAnimation 3s infinite;
	}
	.orange-square {
		background: orange;
		box-shadow: var(--glow-orange);
	}

	/* this is for green square lmao lol rofl...
	wtf am i typing */
	@keyframes squareAnimation {
		0% {
			transform: rotate(0deg);
		}
		33% {
			transform: rotate(45deg);
		}
		66% {
			transform: rotate(-45deg);
		}
		100% {
			transform: rotate(0deg);
		}
	}
</style>
