<script>
	import Button from './Button.svelte';
</script>

<header class="flex-between-row">
	<p><span></span> mccoords</p>
</header>

<style>
	header {
		position: fixed;
		width: min(100%, 1200px);
		padding: calc(var(--spacing-lg) * 2);
		p {
			color: white;
			font-weight: bold;

			span {
				display: block;
				width: 16px;
				height: 16px;
				background-color: greenyellow;
				border-radius: 4px;
				box-shadow: 0 0 20px 1px greenyellow;
			}
		}
	}
</style>
