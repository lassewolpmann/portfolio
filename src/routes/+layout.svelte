<script lang="ts">
	import '../app.css';
	import NavBar from '$lib/components/NavBar.svelte';

	let { children } = $props();
</script>

<style>
	:global(html) {
			box-sizing: border-box;
      background-color: var(--color-gray-50);

      transition-property: background-color;
      transition-timing-function: var(--tw-ease, var(--default-transition-timing-function));
      transition-duration: var(--tw-duration, var(--default-transition-duration));

      &.dark {
          background-color: var(--color-gray-950);
      }
	}

	:global(body) {
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: flex-start;
	}
</style>

<NavBar />
<div id="main" class="text-gray-800 dark:text-gray-200 flex flex-col items-center justify-center gap-16 px-2.5">
	{@render children()}
</div>
