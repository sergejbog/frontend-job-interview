<script lang="ts">
	interface Props {
		items: { id: number; text: string }[];
	}

	const { items }: Props = $props();
</script>

<div class="flex w-full">
	{#each items as item (item.id)}
		<div class="w-1/3 flex-shrink-0 p-4">
			<div class="flex h-24 items-center justify-center rounded-lg bg-gray-700">
				<span class="font-bold text-white">{item.text}</span>
			</div>
		</div>
	{/each}
</div>
