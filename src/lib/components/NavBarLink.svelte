<script lang="ts">
	let { id, text }: {
		id: string,
		text: string
	} = $props();
</script>
<style>

</style>
<a
	href="#{id}"
	class="text-nowrap transition-all hover:text-gray-400 dark:hover:text-gray-600 px-4 py-2 active:bg-gray-50 dark:active:bg-gray-950 active:shadow-xl rounded-full active:text-gray-800 dark:active:text-gray-200"
>{text}</a>