<script lang="ts">
	import TimeLine from '$lib/components/TimeLine.svelte';
</script>

<svelte:head>
	<title>Lasse Wolpmann</title>
</svelte:head>

<article id="about-me" class="prose dark:prose-invert prose-img:rounded-full prose-img:w-64 prose-img:shadow-2xl flex flex-row items-center gap-10">
	<img src="portrait.jpg" alt="Portrait">
	<div>
		<h1>Lasse Wolpmann</h1>
		<h3>Software Developer</h3>
	</div>
</article>

<article id="education" class="prose dark:prose-invert text-nowrap">
	<h1>Education</h1>

	<div class="flex flex-row gap-10">
		<TimeLine start="August 2022" end="August 2025" />

		<section>
			<h2>Turku University of Applied Sciences</h2>
			<h3>B. Eng. Information and Communications Technology</h3>
			<p><a href="https://urn.fi/URN:NBN:fi:amk-2025060921697" target="_blank">Link to Thesis</a></p>
			📍 Turku, Finland
		</section>
	</div>

	<div class="flex flex-row gap-10">
		<TimeLine start="August 2017" end="July 2020" />

		<section>
			<h2>Berufsbildungszentrum Dithmarschen</h2>
			<h3>Computer Science Expert</h3>
			📍 Meldorf, Germany
		</section>
	</div>

	<div class="flex flex-row gap-10">
		<TimeLine start="July 2009" end="June 2017" />

		<section>
			<h2>Meldorfer Gelehrtenschule</h2>
			<h3>High School Diploma</h3>
			📍 Meldorf, Germany
		</section>
	</div>
</article>

<article id="work" class="prose dark:prose-invert text-nowrap">
	<h1>Work Experience</h1>

	<div class="flex flex-row gap-10">
		<TimeLine start="April 2025" end="July 2025" />

		<section>
			<h2>Student Assistant - Smart Brewery</h2>
			<h3>Turun AMK Oy</h3>
			📍 Turku, Finland
		</section>
	</div>

	<div class="flex flex-row gap-10">
		<TimeLine start="September 2021" end="August 2023" />

		<section>
			<h2>Runner and Bartender</h2>
			<h3>The Old Irish Pub</h3>
			📍 Turku, Finland
		</section>
	</div>

	<div class="flex flex-row gap-10">
		<TimeLine start="January 2021" end="June 2021" />

		<section>
			<h2>Conscript</h2>
			<h3>Puolustusvoimat - Finnish Defence Forces</h3>
			📍 Säkylä, Finland
		</section>
	</div>

	<div class="flex flex-row gap-10">
		<TimeLine start="August 2017" end="July 2020" />

		<section id="sys-admin">
			<h2>Systems Administrator (Apprentice)</h2>
			<h3>Evers-Druck GmbH</h3>
			📍 Meldorf, Germany
		</section>
	</div>
</article>

<article id="projects" class="prose dark:prose-invert text-nowrap">
	<h1>Projects</h1>

	<section>
		<h2>formulacountdown.com <a href="https://formulacountdown.com" target="_blank" class="no-underline">🔗</a></h2>
		<h3>Skills</h3>
		<ul>
			<li>SvelteKit</li>
			<li>TypeScript</li>
			<li>(S)CSS</li>
			<li>REST APIs</li>
			<li>Google AdSense Monetization</li>
			<li>SEO Optimization</li>
		</ul>
	</section>

	<section>
		<h2>Formula Countdown (iOS) <a href="https://apps.apple.com/de/app/formula-countdown/id6472580786" target="_blank" class="no-underline">🔗</a></h2>
		<h3>Skills</h3>
		<ul>
			<li>Swift</li>
			<li>SwiftUI</li>
			<li>App Store Deployment</li>
		</ul>
	</section>

	<section>
		<h2>Tic Tac Toe in C <a href="https://github.com/lassewolpmann/tic-tac-toe-c" target="_blank" class="no-underline">🔗</a></h2>
		<h3>Skills</h3>
		<ul>
			<li>Text Input Handling</li>
			<li>CMake Build System</li>
			<li>Working CPU Player (Minimax Algorithm)</li>
		</ul>
	</section>
</article>

<article id="contact" class="prose dark:prose-invert text-nowrap">
	<h1>Contact</h1>
	<p><a href="https://www.linkedin.com/in/lasse-wolpmann/" target="_blank">LinkedIn</a></p>
	<p><a href="https://github.com/lassewolpmann/" target="_blank">GitHub</a></p>
	<p><a href="mailto:lasse@lassewolpmann.com">E-Mail</a></p>
</article>