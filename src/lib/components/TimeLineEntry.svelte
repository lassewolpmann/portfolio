<script lang="ts">
	interface Props {
		name: string,
		description?: string,
		subDescription?: string,
		location?: string,
		start: string,
		end: string,
		url?: string,
		urlDescription?: string,
		tasks?: string[]
	}

	import TimeLine from '$lib/components/TimeLine.svelte';

	let { name, description, subDescription, location, start, end, url, urlDescription, tasks }: Props = $props();
</script>

<div class="flex flex-row items-stretch justify-between gap-2 sm:gap-10 transition-all bg-gray-100 dark:bg-gray-800 pr-2">
	<TimeLine {start} {end} />

	<section class="text-right flex flex-col gap-2">
		<h2 class="text-xl sm:text-2xl font-semibold">{name}</h2>
		{#if description}<h3 class="text-lg sm:text-xl">{description}</h3>{/if}
		{#if subDescription}<h4 class="text-base sm:text-lg">{subDescription}</h4>{/if}

		{#if url && urlDescription}
			<a href={url} target="_blank" class="underline">{urlDescription}</a>
		{/if}

		{#if location}
			📍 {location}
		{/if}

		{#if tasks}
			<h5 class="text-sm sm:text-base font-semibold pt-4">Skills</h5>
			<ul>
				{#each tasks as task (task)}
					<li class="py-1">{task}</li>
				{/each}
			</ul>
		{/if}
	</section>
</div>