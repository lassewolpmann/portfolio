<script lang="ts">
	import '../app.css';
	import { onMount } from 'svelte';
	import NavBarLink from '$lib/components/NavBarLink.svelte';

	let { children } = $props();

	let theme: "dark" | "light" = $state("light");
	let bodyEl: HTMLBodyElement | undefined = $state();
	let navEl: HTMLElement | undefined = $state();
	let scrollY: number = $state(0);
	let innerWidth: number = $state(0);

	let showMenu: boolean = $state(false);

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

<style>
	nav {
      div {
          &.hidden {
              display: none;
          }
      }

			button {
					overflow: hidden;

					span {
							width: 90%;
							transition: transform 0.3s ease;

							&#first {
									top: 10%;
							}

              &#second {
                  top: calc(50% - 2px);
              }

              &#third {
                  bottom: 10%;
              }
					}

					&.closeMenu {
              span#first {
                  top: calc(50% - 2px);
                  transform: rotate(45deg);
              }

              span#second {
                  display: none;
              }

              span#third {
                  top: calc(50% - 2px);
                  transform: rotate(-45deg);
              }
					}
			}
  }
</style>

<svelte:window bind:scrollY={scrollY} bind:innerWidth={innerWidth}></svelte:window>
<svelte:body bind:this={bodyEl}></svelte:body>

<header class="fixed w-full flex items-center justify-center">
	<nav bind:this={navEl} class="bg-gray-100 dark:bg-gray-700 text-gray-400 sm:rounded-full sm:m-4 px-6 py-3 shadow-xl flex flex-col sm:flex-row items-start sm:items-center justify-start gap-5 w-full sm:w-max">
		<button class:closeMenu={showMenu} class="relative cursor-pointer touch-none w-6 h-6 sm:hidden self-end text-2xl" aria-label="Open/Close Navigation Menu" onclick={() => showMenu = !showMenu}>
			<span class="bar h-1 rounded-full bg-gray-700 dark:bg-gray-100 block absolute" id="first"></span>
			<span class="bar h-1 rounded-full bg-gray-700 dark:bg-gray-100 block absolute" id="second"></span>
			<span class="bar h-1 rounded-full bg-gray-700 dark:bg-gray-100 block absolute" id="third"></span>
		</button>
		<div class="flex flex-col sm:flex-row items-start sm:items-center justify-start gap-5" class:hidden={!showMenu && innerWidth < 640}>
			<NavBarLink id="" text="Home" />
			<NavBarLink id="education" text="Education" />
			<NavBarLink id="work" text="Work Experience" />
			<NavBarLink id="projects" text="Projects" />
			<NavBarLink id="contact" text="Contact" />
			<button class="cursor-pointer bg-gray-200 dark:bg-gray-600 rounded-full w-10 aspect-square" onclick={setTheme}>{theme === "light" ? "🌑" : "☀️"}</button>
		</div>
	</nav>
</header>
<main class="bg-gray-50 dark:bg-gray-950 transition-colors px-8 py-16 flex flex-col gap-32 items-start justify-start">
	{@render children()}
</main>
