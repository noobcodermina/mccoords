<script lang="ts">
	import type { HTMLButtonAttributes } from 'svelte/elements';
	import type { Snippet } from 'svelte';

	interface BtnProps extends HTMLButtonAttributes {
		children: Snippet;
		smallGlow?: boolean;
	}

	let { children, smallGlow, ...rest }: BtnProps = $props();
</script>

<button class="flex-center-row" class:small-glow={smallGlow} {...rest}>{@render children()}</button>

<style>
	button {
		background: var(--white-bg);
		padding: var(--spacing-lg) calc(var(--spacing-lg) * 2);
		border: var(--border-black);
		border-radius: var(--radius-lg);
		box-shadow: var(--glow-grey);
		font-weight: var(--text-bold);
		gap: var(--spacing-lg);
		cursor: pointer;
		transition: var(--transition);
		&:hover {
			transform: scale(0.98);
		}
	}
	.small-glow {
		box-shadow: var(--glow-grey-small);
	}
</style>
