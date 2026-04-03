<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>

<nav class="flex justify-center space-x-4 p-4 bg-gray-100 dark:bg-neutral-800">
	<a href="/" class="text-blue-600 hover:text-blue-800 dark:text-blue-400 dark:hover:text-blue-300">Latest</a>
	<a href="/pinned" class="text-blue-600 hover:text-blue-800 dark:text-blue-400 dark:hover:text-blue-300">Pinned</a>
	<a href="/about" class="text-blue-600 hover:text-blue-800 dark:text-blue-400 dark:hover:text-blue-300">About</a>
</nav>

<div class="max-w-4xl mx-auto p-4">
	{@render children()}
</div>
