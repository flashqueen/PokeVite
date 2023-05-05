<script setup>
import { onMounted, reactive, ref, computed } from "vue";
import ListPokemons from "../components/ListPokemons.vue"
import CardPokemonSelected from "../components/CardPokemonSelected.vue"

let urlBaseSvg = ref("https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/")
let pokemons = reactive(ref());
let searchPokemonField = ref("");
let pokemonSelected = reactive(ref());
let loading = ref(false)

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=251&offset=0")
    .then(res => res.json())
    .then(res => pokemons.value = res.results);

})

const pokemonsFiltered = computed(() => {
  if (pokemons.value && searchPokemonField.value) {
    return pokemons.value.filter(pokemon =>
      pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase())
    )
  }
  return pokemons.value;
})

const selectPokemon = async (pokemon) => {
  loading.value = true;
  await fetch(pokemon.url)
    .then(res => res.json())
    .then(res => pokemonSelected.value = res)
    .catch(err => alert(err))
    .finally(() => loading.value = false)
}
</script>

<template>
  <main>
    <div class="container text-center text-body-secondary">
      <div class="row mt-4">
        <div class="col-sm-12 col-md-6">
          <CardPokemonSelected :name="pokemonSelected?.name" :exp="pokemonSelected?.base_experience"
            :weight="pokemonSelected?.weight" :height="pokemonSelected?.height"
            :img="pokemonSelected?.sprites.other.dream_world.front_default" :loading="loading" />

        </div>
        <div class="col-sm-12 col-md-6">
          <div class="mb-3">
            <label hidden for="searchPokemonField" class="form-label">Pesquisar...</label>
            <input v-model="searchPokemonField" type="text" class="form-control" id="searchPokemonField"
              placeholder="Ex: chikorita, ditto, mew...">
          </div>
          <div class="card card-list">
            <div class="card-body row">
              <ListPokemons v-for="pokemon in pokemonsFiltered" :key="pokemon.name" :name="pokemon.name"
                :urlBaseSvg="urlBaseSvg + pokemon.url.split('/')[6] + '.svg'" @click="selectPokemon(pokemon)" />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.card-list {
  max-height: 75vh;
  overflow-y: scroll;
  overflow-x: hidden;
}
</style>