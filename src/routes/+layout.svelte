<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import CustomCursor from '$lib/components/CustomCursor.svelte';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>White Lace & Promises - Wedding & Event Styling</title>
	<meta
		name="description"
		content="White Lace & Promises is a wedding and event styling studio creating elegant celebrations with planning, consulting, design and execution."
	/>
	<meta property="og:title" content="White Lace & Promises - Wedding & Event Styling" />
	<meta
		property="og:description"
		content="Where your story becomes something timeless. Weddings, corporate galas and celebrations styled with meticulous attention to every detail."
	/>
	<meta property="og:type" content="website" />
	<meta name="theme-color" content="#0a0a0a" />
</svelte:head>

<CustomCursor />

{@render children()}
