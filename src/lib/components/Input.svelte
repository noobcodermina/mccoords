<script lang="ts">
	import type { HTMLInputAttributes } from 'svelte/elements';

	let { value = $bindable(), ...rest }: HTMLInputAttributes = $props();
</script>

<input bind:value {...rest} />

<style>
	input {
		padding: var(--spacing-lg);
		background: var(--dark-gray);
		color: var(--text-primary);
		border: var(--border-gray);
		border-radius: var(--radius-sm);
		font: inherit;
	}
</style>
