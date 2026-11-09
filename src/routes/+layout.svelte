<script lang="ts">
	import '../app.css';

	import Header from '#lib/components/Header.svelte';

	import favicon from '#lib/assets/favicon.svg';
	import type { LayoutProps } from './$types';

	let { children }: LayoutProps = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>
<div class="page-wrapper">
	<Header></Header>
	{@render children()}
</div>

<style>
	.page-wrapper {
		width: min(100%, 1200px);
		margin: auto;
	}
</style>
