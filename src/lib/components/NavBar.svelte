<script lang="ts">
	import NavBarLink from '$lib/components/NavBarLink.svelte';
	import { onMount } from 'svelte';

	let showMenu: boolean = $state(false);
	let theme: "dark" | "light" = $state("light");
	let navEl: HTMLElement | undefined = $state();
	let innerWidth: number = $state(0);
	let lastScrollEvent: number = Date.now();

	const toggleTheme = () => {
		const htmlEl = document.getElementsByTagName("html").item(0);

		if (!htmlEl) return;

		switch (theme) {
			case "dark": {
				theme = "light";
				htmlEl.classList.remove("dark");

				break;
			}
			case "light": {
				theme = "dark";
				htmlEl.classList.add("dark");

				break;
			}
		}
	}

	const getActiveNavElement = () => {
		const mainEl = document.getElementById("main");

		if (!navEl) return;
		if (!mainEl) return;

		const contentChildrenCount = mainEl.childElementCount;
		const contentChildren = mainEl.children;

		const navLinkElements = navEl.getElementsByTagName("a");

		let activeIndex = 0;

		for (let i = 0; i < contentChildrenCount; i++) {
			const childEl = contentChildren.item(i);
			if (!childEl) continue;

			childEl.classList.remove("active");

			const childY = childEl.getBoundingClientRect().y;
			const navBarScrollMargin = 128;

			if (childY - navBarScrollMargin > 0) {
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
	}

	const handleScroll = () => {
		const eventTimestamp = Date.now();
		if (eventTimestamp - lastScrollEvent < 100) return;	// Throttle event to every 100ms

		lastScrollEvent = eventTimestamp;
		getActiveNavElement();
	}

	onMount(() => {
		getActiveNavElement();

		const htmlEl = document.getElementsByTagName("html").item(0);

		if (!window.matchMedia("(prefers-color-scheme: dark)").matches) return;
		if (!htmlEl) return;

		htmlEl.classList.add("dark");
		theme = "dark";
	})
</script>
<style>
    nav {
        button {
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
<svelte:window onscroll={handleScroll} bind:innerWidth={innerWidth}></svelte:window>
<div id="header" class="fixed w-full flex items-center justify-center text-gray-600 dark:text-gray-400">
	<nav bind:this={navEl} class="bg-gray-100 dark:bg-gray-900 sm:rounded-full sm:m-4 px-6 py-3 shadow-lg flex flex-col sm:flex-row items-start sm:items-center justify-start gap-5 w-full sm:w-max">
		<button class:closeMenu={showMenu} class="relative cursor-pointer touch-none w-6 h-6 sm:hidden self-end text-2xl" aria-label="Open/Close Navigation Menu" onclick={() => showMenu = !showMenu}>
			<span class="bar h-1 rounded-full bg-gray-700 dark:bg-gray-100 block absolute" id="first"></span>
			<span class="bar h-1 rounded-full bg-gray-700 dark:bg-gray-100 block absolute" id="second"></span>
			<span class="bar h-1 rounded-full bg-gray-700 dark:bg-gray-100 block absolute" id="third"></span>
		</button>
		<div class="flex flex-col sm:flex-row items-start sm:items-center justify-start hide:hidden" class:hide={!showMenu && innerWidth < 640}>
			<NavBarLink id="" text="Home" />
			<NavBarLink id="education" text="Education" />
			<NavBarLink id="work" text="Work Experience" />
			<NavBarLink id="projects" text="Projects" />
			<NavBarLink id="contact" text="Contact" />
			<button class="my-5 sm:mx-5 sm:my-0 cursor-pointer bg-gray-200 dark:bg-gray-600 rounded-full w-10 aspect-square" onclick={toggleTheme}>{theme === "light" ? "🌑" : "☀️"}</button>
		</div>
	</nav>
</div>