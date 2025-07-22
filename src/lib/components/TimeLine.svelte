<script lang="ts">
	let { start, end }: {
		start: string,
		end: string
	} = $props();
</script>
<div class="flex flex-col items-start justify-between border-l-2 border-solid border-l-gray-300 px-5 sm:text-nowrap">
	<span>{end}</span>
	<span>{start}</span>
</div>