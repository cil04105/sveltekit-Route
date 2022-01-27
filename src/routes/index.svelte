<script>
	import { pokemon } from '../stores/pokestore';
	import PokemanCard from '../components/pokemanCard.svelte';

	let searchPokemon = '';
	let filteredPokemon = [];
	$: {
		if (searchPokemon) {
			filteredPokemon = $pokemon.filter((pokeman) =>
				pokeman.name.toLowerCase().includes(searchPokemon.toLowerCase())
			);
		} else {
			filteredPokemon = [...$pokemon];
		}
	}
</script>

<svelte:head>
	<title>sveltekit-pokedex</title>
</svelte:head>
<h1 class="text-4xl text-center my-8 uppercase">SvelteKit-pokedex</h1>
<input
	class="w-full rounded-md p-4 bg-gray-100 border-2 border-gray-200"
	type="text"
	placeholder="Search Pokemon"
	bind:value={searchPokemon}
/>
<div class="py-8 grid gap-4 md:grid-cols-2 grid-cols-1">
	{#each filteredPokemon as pokeman}
		<!-- <p class="">{pokeman.name}</p> -->
		<PokemanCard {pokeman} />
	{/each}
</div>
