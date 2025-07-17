<script lang="ts">
	import '../app.css';
	import { onMount } from 'svelte';

	let { children } = $props();

	let theme: "dark" | "light" = $state("light");
	let bodyEl: HTMLBodyElement;

	onMount(() => {
		if (!window.matchMedia("(prefers-color-scheme: dark)").matches) return;

		bodyEl.classList.add("dark");
		theme = "dark";
	})

	const setTheme = () => {
		switch (theme) {
			case "dark": {
				theme = "light";
				bodyEl.classList.remove("dark");

				break;
			}
			case "light": {
				theme = "dark";
				bodyEl.classList.add("dark");

				break;
			}
		}
	}
</script>

<svelte:body bind:this={bodyEl}></svelte:body>
<header class="fixed w-full flex items-center justify-center">
	<nav class="bg-gray-100 dark:bg-gray-700 text-gray-400 text-lg rounded-full m-4 px-6 py-3 shadow-xl flex flex-row items-center justify-center gap-5 w-max">
		<a href="#about-me" class="hover:text-gray-900 dark:hover:text-gray-100">Home</a>
		<a href="#education" class="hover:text-gray-900 dark:hover:text-gray-100">Education</a>
		<a href="#work" class="hover:text-gray-900 dark:hover:text-gray-100">Work Experience</a>
		<a href="#projects" class="hover:text-gray-900 dark:hover:text-gray-100">Projects</a>
		<a href="#contact" class="hover:text-gray-900 dark:hover:text-gray-100">Contact</a>
		<button class="cursor-pointer bg-gray-200 dark:bg-gray-500 rounded-full w-10 aspect-square" onclick={setTheme}>{theme === "dark" ? "🌑" : "☀️"}</button>
	</nav>
</header>
<main class="bg-gray-50 dark:bg-gray-950 transition-colors px-4 py-16">
	{@render children()}
</main>
