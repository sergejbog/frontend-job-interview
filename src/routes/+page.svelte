<script lang="ts">
	import Carousel from './Carousel.svelte';

  let items = [
		{ id: 1, text: 'Logo A' },
		{ id: 2, text: 'Logo B' },
		{ id: 3, text: 'Logo C' },
		{ id: 4, text: 'Logo D' },
		{ id: 5, text: 'Logo E' }
	];
</script>

<main class="mx-auto w-full max-w-lg py-8">
	<h1 class="mt-20 text-center text-4xl text-gray-400">Carousel Coding Challenge</h1>

	<div class="relative w-full overflow-hidden mt-20">
		<Carousel {items}/>
	</div>
</main>
