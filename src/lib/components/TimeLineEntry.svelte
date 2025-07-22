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

	let timeLineEntryDiv: HTMLDivElement | undefined = $state();
	let innerHeight: number = $state(0);
	let lastScrollEvent: number = Date.now();

	const handleScroll = () => {
		if (!timeLineEntryDiv) return;

		const eventTimestamp = Date.now();
		if (eventTimestamp - lastScrollEvent < 100) return;	// Throttle event to every 100ms

		lastScrollEvent = eventTimestamp;

		const { y } = timeLineEntryDiv.getBoundingClientRect();
		const distanceFromBottomOfScreen = (y - innerHeight) * -1;
		const normalizedDistance = distanceFromBottomOfScreen / innerHeight;

		timeLineEntryDiv.style.opacity = (normalizedDistance + 0.35).toString();
	}
</script>

<svelte:window onscroll={handleScroll} bind:innerHeight={innerHeight}></svelte:window>
<div class="flex flex-row items-stretch justify-between gap-2 sm:gap-10 transition-all" bind:this={timeLineEntryDiv}>
	<TimeLine {start} {end} />

	<section class="text-right flex flex-col gap-2">
		<h2 class="text-xl sm:text-2xl font-semibold">{name}</h2>
		<h3 class="text-lg sm:text-xl">{description}</h3>
		<h4 class="text-base sm:text-lg">{subDescription}</h4>

		{#if url && urlDescription}
			<p><a href={url} target="_blank" class="underline">{urlDescription}</a></p>
		{/if}

		{#if location}
			📍 {location}
		{/if}

		{#if tasks}
			<h5 class="text-sm sm:text-base font-semibold">Skills</h5>
			<ul>
				{#each tasks as task (task)}
					<li class="py-1">{task}</li>
				{/each}
			</ul>
		{/if}
	</section>
</div>