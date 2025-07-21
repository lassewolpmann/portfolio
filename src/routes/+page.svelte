<script lang="ts">
	import TimeLineEntry from '$lib/components/TimeLineEntry.svelte';
	import Project from '$lib/components/Project.svelte';
</script>

<svelte:head>
	<title>Lasse Wolpmann</title>
</svelte:head>

<div id="content" class="transition-colors px-8 py-16 sm:py-32 flex flex-col gap-16">
	<article id="about-me" class="flex flex-row items-center justify-between gap-2 sm:gap-10 w-full">
		<img src="portrait.jpg" alt="Portrait" class="rounded-full w-24 sm:w-64 shadow-2xl">
		<div class="text-right">
			<h1 class="text-2xl sm:text-3xl font-bold">Lasse Wolpmann</h1>
			<h3 class="text-lg sm:text-2xl">Software Developer</h3>
		</div>
	</article>

	<article id="education" class="flex flex-col gap-10 w-full">
		<h1 class="text-2xl sm:text-3xl font-bold">Education</h1>

		<TimeLineEntry
			name="Turku University of Applied Sciences"
			description="B. Eng. Information and Communications Technology"
			location="Turku, Finland"
			start="August 2022"
			end="August 2025"
			url="https://urn.fi/URN:NBN:fi:amk-2025060921697"
			urlDescription="Link to Thesis"
		/>

		<TimeLineEntry
			name="BBZ Dithmarschen"
			description="Computer Science Expert"
			location="Meldorf, Germany"
			start="August 2017"
			end="July 2020"
		/>

		<TimeLineEntry
			name="Meldorfer Gelehrtenschule"
			description="High School Diploma"
			location="Meldorf, Germany"
			start="July 2009"
			end="June 2017"
		/>
	</article>

	<article id="work" class="flex flex-col gap-10 w-full">
		<h1 class="text-2xl sm:text-3xl font-bold">Work Experience</h1>

		<TimeLineEntry
			name="Student Assistant - Smart Brewery"
			description="Turun AMK Oy"
			location="Turku, Finland"
			start="April 2025"
			end="July 2025"
		/>

		<TimeLineEntry
			name="Runner and Bartender"
			description="The Old Irish Pub"
			location="Turku, Finland"
			start="September 2021"
			end="August 2023"
		/>

		<TimeLineEntry
			name="Conscript"
			description="Finnish Defence Forces"
			location="Säkylä, Finland"
			start="January 2021"
			end="June 2021"
		/>

		<TimeLineEntry
			name="Systems Administrator (Apprentice)"
			description="Evers-Druck GmbH"
			location="Meldorf, Germany"
			start="August 2017"
			end="July 2020"
		/>
	</article>

	<article id="projects" class="flex flex-col gap-10 w-full">
		<h1 class="text-2xl sm:text-3xl font-bold">Projects</h1>

		<Project
			name="formulacountdown.com"
			url="https://formulacountdown.com"
			skills={[
			"SvelteKit",
			"TypeScript",
			"CSS",
			"REST APIs",
			"Google AdSense Monetization",
			"SEO Optimization"
		]}
		/>

		<Project
			name="Formula Countdown (iOS)"
			url="https://apps.apple.com/de/app/formula-countdown/id6472580786"
			skills={[
			"Swift",
			"SwiftUI",
			"App Store Deployment"
		]}
		/>

		<Project
			name="Tic Tac Toe in C"
			url="https://github.com/lassewolpmann/tic-tac-toe-c"
			skills={[
			"Text Input Handling",
			"CMake Build System",
			"Working CPU Player (Minimax Algorithm)"
		]}
		/>
	</article>

	<article id="contact" class="flex flex-col gap-2 w-full">
		<h1 class="text-2xl sm:text-3xl font-bold">Contact</h1>
		<p><a href="https://www.linkedin.com/in/lasse-wolpmann/" target="_blank" class="underline">LinkedIn</a></p>
		<p><a href="https://github.com/lassewolpmann/" target="_blank" class="underline">GitHub</a></p>
		<p><a href="mailto:lasse@lassewolpmann.com" class="underline">E-Mail</a></p>
	</article>
</div>