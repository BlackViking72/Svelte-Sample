<script>
    import {pokemon} from "../store/pokestore";
    import PokemanCard from "../components/pokemanCard.svelte";

    let searchTerm = "";
    let filteredPokemon = [];

    $ : {
        if (searchTerm)
            filteredPokemon = $pokemon.filter(pokeman => {
                return pokeman.name.toLowerCase().includes(searchTerm.toLowerCase())
            })
        else
            filteredPokemon = [...$pokemon]
    }
</script>
<svelte:head>
    <title>Svelte Kit Pokedex</title>
</svelte:head>
<h1 class="text-4xl text-center my-8 uppercase">Svelte Kit Pokedex</h1>

<input type="text" placeholder="Search pokemon" bind:value={searchTerm} class="w-full rounded-md text-lg border-2 border-gray-200 p-4">

<div class="py-6 grid md:grid-cols-2 grid-cols-1 gap-4 my-2">
    {#each filteredPokemon as pokeman}
        <PokemanCard pokeman={pokeman}/>
    {/each}
</div>