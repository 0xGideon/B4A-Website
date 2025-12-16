<script lang="ts">
	import '../app.css';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href="/favicon.ico" sizes="any" />
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
	<link
		rel="preload"
		as="style"
		href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;600&family=Poppins:wght@600;700&display=swap"
	/>
	<link
		rel="stylesheet"
		href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;600&family=Poppins:wght@600;700&display=swap"
		media="print"
		onload={(e) => (((e.currentTarget as HTMLLinkElement) || e.target) as HTMLLinkElement).media = 'all'}
	/>
	<noscript>
		<link
			rel="stylesheet"
			href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;600&family=Poppins:wght@600;700&display=swap"
		/>
	</noscript>
</svelte:head>

{@render children()}
