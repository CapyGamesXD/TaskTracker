<script lang="ts">
	import './layout.css';
	import favicon from '/src/lib/assets/favicon.png';

	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>
{@render children()}
