<script lang="ts">
	import '../app.css';

	let { children } = $props();
</script>
<header class="sticky top-0">
	<nav class="bg-gray-100 opacity-95 p-4 flex flex-row items-start gap-5">
		<a href="#about-me">Home</a>
		<a href="#education">Education</a>
		<a href="#work">Work Experience</a>
		<a href="#projects">Projects</a>
		<a href="#contact">Contact</a>
	</nav>
</header>
<main class="bg-gray-50 p-4">
	{@render children()}
</main>
