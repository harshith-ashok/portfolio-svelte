<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import { dev } from '$app/environment';
	import { injectAnalytics } from '@vercel/analytics/sveltekit';

	injectAnalytics({ mode: dev ? 'development' : 'production' });
	import '../app.css';
	import { page } from '$app/stores';
	const menuItems = [
		{ name: 'Home', path: '/' },
		{ name: 'About', path: '/about' },
		{ name: 'Projects', path: '/projects' },
		{ name: 'Contact', path: '/contact' }
	];
	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<main class="h-screen">
	<div class="">
		<slot />
	</div>
</main>
