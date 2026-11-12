<script lang="ts">
	import type { HTMLButtonAttributes } from 'svelte/elements';
	import type { Snippet } from 'svelte';

	interface BtnProps extends HTMLButtonAttributes {
		children: Snippet;
		smallGlow?: boolean;
		discord?: boolean;
	}

	let { children, discord, smallGlow, ...rest }: BtnProps = $props();
</script>

<button class="flex-center-row" class:discordBtn={discord} class:small-glow={smallGlow} {...rest}
	>{@render children()}</button
>

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
	.discordBtn {
		background-color: var(--blue);
		color: var(--text-primary);
		box-shadow: var(--glow-blue-small);
	}
</style>
