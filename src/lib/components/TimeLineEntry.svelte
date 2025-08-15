<script lang="ts">
	interface ProjectLink {
		url: string,
		desc: string
	}

	interface Props {
		name: string,
		description?: string,
		subDescription?: string,
		location?: string,
		start: string,
		end: string,
		projectLinks?: ProjectLink[]
		tasks?: string[]
	}

	import TimeLine from '$lib/components/TimeLine.svelte';

	let { name, description, subDescription, location, start, end, projectLinks, tasks }: Props = $props();
</script>

<div class="flex flex-row items-stretch justify-between gap-2 sm:gap-10 transition-all bg-gray-100 dark:bg-gray-800 px-6 py-4 rounded-xl">
	<TimeLine {start} {end} />

	<section class="text-right flex flex-col gap-2">
		<h2 class="text-xl sm:text-2xl font-semibold">{name}</h2>
		{#if description}<h3 class="text-lg sm:text-xl">{description}</h3>{/if}
		{#if subDescription}<h4 class="text-base sm:text-lg">{subDescription}</h4>{/if}

		{#if projectLinks && projectLinks.length > 0}
			{#each projectLinks as projectLink (projectLink)}
				<a href={projectLink.url} target="_blank" class="underline">{projectLink.desc}</a>
			{/each}
		{/if}

		{#if location}
			📍 {location}
		{/if}

		{#if tasks}
			<div class="skills mt-4 bg-gray-200 dark:bg-gray-700 px-3 py-1 rounded-xl">
				<h3 class="text-lg sm:text-xl">Skills</h3>
				<ul>
					{#each tasks as task (task)}
						<li class="py-1">{task}</li>
					{/each}
				</ul>
			</div>
		{/if}
	</section>
</div>