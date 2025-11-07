<script lang="ts">
	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href="/assets/yellow-shuttle-logo-512px.jpg" />
</svelte:head>

{@render children()}
