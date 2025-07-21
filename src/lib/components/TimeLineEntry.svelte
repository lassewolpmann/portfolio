<script lang="ts">
	interface Props {
		name: string,
		description: string,
		location: string,
		start: string,
		end: string,
		url?: string,
		urlDescription?: string
	}
	import TimeLine from '$lib/components/TimeLine.svelte';

	let { name, description, location, start, end, url, urlDescription }: Props = $props();
</script>

<div class="flex flex-row items-stretch justify-between gap-2 sm:gap-10">
	<TimeLine {start} {end} />

	<section class="text-right flex flex-col gap-2">
		<h2 class="text-xl sm:text-2xl font-semibold">{name}</h2>
		<h3 class="text-lg sm:text-xl">{description}</h3>
		{#if url && urlDescription}
			<p><a href={url} target="_blank" class="underline">{urlDescription}</a></p>
		{/if}
		📍 {location}
	</section>
</div>