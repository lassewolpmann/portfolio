<script lang="ts">
	import '../app.css';
	import { onMount } from 'svelte';
	import NavBarLink from '$lib/components/NavBarLink.svelte';

	let { children } = $props();

	let theme: "dark" | "light" = $state("light");
	let bodyEl: HTMLBodyElement | undefined = $state();
	let navEl: HTMLElement | undefined = $state();
	let scrollY: number = $state(0);

	onMount(() => {
		if (!window.matchMedia("(prefers-color-scheme: dark)").matches) return;
		if (!bodyEl) return;

		bodyEl.classList.add("dark");
		theme = "dark";
	})

	$effect(() => {
		if (!scrollY) return;
		if (!bodyEl) return;
		if (!navEl) return;

		const mainEl = bodyEl.getElementsByTagName("main").item(0);
		if (!mainEl) return;

		const mainChildrenCount = mainEl.childElementCount;
		const mainChildren = mainEl.children;

		const navLinkElements = navEl.getElementsByTagName("a");

		let activeIndex = 0;

		for (let i = 0; i < mainChildrenCount; i++) {
			const childEl = mainChildren.item(i);
			if (!childEl) continue;

			childEl.classList.remove("active");

			const childY = childEl.getBoundingClientRect().y;

			if (childY > 0) {
				break;
			}

			activeIndex = i;
		}

		[...navLinkElements].forEach(el => {
			el.classList.remove("active");
		})

		const activeLinkEl = navLinkElements.item(activeIndex);
		if (!activeLinkEl) return;

		activeLinkEl.classList.add("active");
	});

	const setTheme = () => {
		if (!bodyEl) return;

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

<svelte:window bind:scrollY={scrollY}></svelte:window>
<svelte:body bind:this={bodyEl}></svelte:body>
<header class="fixed w-full flex items-center justify-center">
	<nav bind:this={navEl} class="bg-gray-100 dark:bg-gray-700 text-gray-400 text-lg rounded-full m-4 px-6 py-3 shadow-xl flex flex-row items-center justify-center gap-5 w-max">
		<NavBarLink id="about-me" text="Home" />
		<NavBarLink id="education" text="Education" />
		<NavBarLink id="work" text="Work Experience" />
		<NavBarLink id="projects" text="Projects" />
		<NavBarLink id="contact" text="Contact" />
		<button class="cursor-pointer bg-gray-200 dark:bg-gray-700 rounded-full w-10 aspect-square" onclick={setTheme}>{theme === "dark" ? "🌑" : "☀️"}</button>
	</nav>
</header>
<main class="bg-gray-50 dark:bg-gray-950 transition-colors px-8 py-16 flex flex-col gap-32 items-start justify-start">
	{@render children()}
</main>
