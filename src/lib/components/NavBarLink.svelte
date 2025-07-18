<script lang="ts">
	let { id, text }: {
		id: string,
		text: string
	} = $props();
</script>
<a href="#{id}" class="active:text-gray-700 dark:active:text-gray-100 hover:text-gray-500 dark:hover:text-gray-300">{text}</a>