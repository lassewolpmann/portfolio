<script lang="ts">
	interface Props {
		name: string,
		url: string,
		skills: string[]
	}

	let { name, url, skills }: Props = $props();
</script>

<section>
	<h2 class="text-xl sm:text-2xl font-semibold">{name} <a href={url} target="_blank" class="no-underline">🔗</a></h2>
	<ul class="list-disc">
		{#each skills as skill (skill)}
			<li class="ml-5">{skill}</li>
		{/each}
	</ul>
</section>