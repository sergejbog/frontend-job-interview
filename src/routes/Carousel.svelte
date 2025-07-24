<script lang="ts">
  import { onMount, tick } from "svelte";

  export let items: { id: number; text: string }[];

  let localItems: { id: number; text: string }[] = [];
  let offset = 0;
  let firstBlock!: HTMLDivElement;
  let blockWidth = 0;

  onMount(async () => {
    localItems = [...items]; 
    await tick();
    blockWidth = firstBlock.clientWidth;
    setInterval(() => {
      offset += 1;
      if (offset >= blockWidth) {
        offset = 0;
        const first = localItems.shift();
        if (first) localItems.push(first);
      }
    }, 10);
  });
</script>

<style>
  .carousel { overflow: hidden; width: 100%; }
  .inner {
    display: flex;
    transition: transform 0.01s linear;
    will-change: transform;
  }
  .block {
    flex-shrink: 0;
    width: 33.333%;
    padding: 1rem;
  }
</style>

<div class="carousel">
  <div class="inner" style="transform: translateX(-{offset}px);">
    {#each localItems as item, i (item.id)}
      <div class="block" bind:this={firstBlock}>
        <div class="flex h-24 items-center justify-center rounded-lg bg-gray-700">
          <span class="font-bold text-white">{item.text}</span>
        </div>
      </div>
    {/each}
  </div>
</div>