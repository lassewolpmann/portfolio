<script lang="ts">
	import TimeLineEntry from '$lib/components/TimeLineEntry.svelte';
</script>

<article id="about-me" class="flex flex-row items-center justify-between gap-2 sm:gap-10 w-full min-h-svh">
	<img src="portrait.jpg" alt="Portrait" class="rounded-full w-24 sm:w-64 shadow-2xl">
	<div class="text-right">
		<h1 class="text-2xl sm:text-4xl font-bold">Lasse Wolpmann</h1>
		<h3 class="text-lg sm:text-2xl font-semibold">Software Developer</h3>
		<h5 class="text-sm sm:text-lg">Embedded, iOS, Web</h5>
	</div>
</article>

<article id="education" class="flex flex-col gap-10 w-ful min-h-svh scroll-m-16 sm:scroll-m-32">
	<h1 class="text-2xl sm:text-3xl font-bold">Education</h1>

	<TimeLineEntry
		name="Turku University of Applied Sciences"
		description="B. Eng. Information and Communications Technology"
		subDescription="Embedded Software and IoT"
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

<article id="work" class="flex flex-col gap-10 w-full min-h-svh scroll-m-16 sm:scroll-m-32">
	<h1 class="text-2xl sm:text-3xl font-bold">Work Experience</h1>

	<TimeLineEntry
		name="Student Assistant - Smart Brewery"
		description="Turun AMK Oy"
		location="Turku, Finland"
		start="April 2025"
		end="July 2025"
		tasks={[
			"SPI and I2C Communication between ESP32 and BME688",
			"Read datasheets and write custom driver code in C/C++",
			"Memory management",
			"Write a basic HTTP Server in C"
		]}
	/>

	<TimeLineEntry
		name="Bartender"
		description="The Old Irish Pub"
		location="Turku, Finland"
		start="May 2023"
		end="August 2023"
		tasks={[
			"Serve guests",
			"Give advice on drink choices",
			"Be the face of the establishment"
		]}
	/>

	<TimeLineEntry
		name="Runner"
		description="The Old Irish Pub"
		location="Turku, Finland"
		start="September 2021"
		end="July 2022"
		tasks={[
			"Provide equipment to bartenders",
			"Ensure a clean bar environment",
			"Keep up smooth communication between coworkers"
		]}
	/>

	<TimeLineEntry
		name="Conscript"
		description="Finnish Defence Forces"
		location="Säkylä, Finland"
		start="January 2021"
		end="June 2021"
		tasks={[
			"Integrate into a completely new environment",
			"Respect authority and sticking to a tight schedule",
			"Take on leadership roles",
			"Endure harsh environments"
		]}
	/>

	<TimeLineEntry
		name="Systems Administrator (Apprentice)"
		description="Evers-Druck GmbH"
		location="Meldorf, Germany"
		start="August 2017"
		end="July 2020"
		tasks={[
			"Work in a professional office environment",
			"Fix real-life problems"
		]}
	/>
</article>

<article id="projects" class="flex flex-col gap-10 w-full min-h-svh scroll-m-16 sm:scroll-m-32">
	<h1 class="text-2xl sm:text-3xl font-bold">Projects</h1>

	<TimeLineEntry
		name="Tic Tac Toe in C"
		start="July 2025"
		end="ongoing"
		url="https://github.com/lassewolpmann/tic-tac-toe-c"
		urlDescription="GitHub repository"
		tasks={[
			"Text Input Handling",
			"CMake Build System",
			"Working CPU Player (Minimax Algorithm)"
		]}
	/>

	<TimeLineEntry
		name="Formula Countdown (iOS)"
		start="November 2023"
		end="ongoing"
		url="https://apps.apple.com/de/app/formula-countdown/id6472580786"
		urlDescription="App Store"
		tasks={[
			"Swift",
			"SwiftUI",
			"App Store Deployment"
		]}
	/>

	<TimeLineEntry
		name="formulacountdown.com"
		start="October 2022"
		end="ongoing"
		url="https://formulacountdown.com"
		urlDescription="GitHub repository"
		tasks={[
			"SvelteKit",
			"TypeScript",
			"CSS",
			"REST APIs",
			"Google AdSense Monetization",
			"SEO Optimization"
		]}
	/>
</article>

<article id="contact" class="flex flex-col gap-2 w-full min-h-svh scroll-m-16 sm:scroll-m-32">
	<h1 class="text-2xl sm:text-3xl font-bold">Contact</h1>
	<p><a href="https://www.linkedin.com/in/lasse-wolpmann/" target="_blank" class="underline">LinkedIn</a></p>
	<p><a href="https://github.com/lassewolpmann/" target="_blank" class="underline">GitHub</a></p>
	<p><a href="mailto:lasse@lassewolpmann.com" class="underline">E-Mail</a></p>
</article>
