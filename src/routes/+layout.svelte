<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
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
	<nav class="px-20 py-10 flex flex-col md:flex-row md:gap-40 items-center gap-10 justify-between">
		<a
			class="text-2xl tracking-wider uppercase font-gsans bg-black px-3 py-1 text-white font-black hover:scale-105 transition-all duration-230"
			href="/">Harshith Ashok</a
		>
		<div class="flex gap-5">
			{#each menuItems as item}
				<a
					href={item.path}
					class="text-sm pb-1 leading-none transition-all uppercase font-gsans tracking-wider duration-230 hover:bg-black p-1 hover:text-white"
					class:border-b-2={item.path === $page.url.pathname}
					class:border-black={item.path === $page.url.pathname}
					class:text-black={item.path === $page.url.pathname}
					class:border-b-1={item.path !== $page.url.pathname}
					class:text-gray-600={item.path !== $page.url.pathname}
				>
					{item.name}
				</a>
			{/each}
		</div>
	</nav>
	<div class="pl-20 pt-10">
		{@render children()}
	</div>
</main>
