<template>
  <div class="justify-space-between py-3 " :class="mobile ? '' : 'd-flex'">
    <v-container class="align-self-center">
    <CardPokemonSelected :name="pokemonSelected?.name"
      :xp="pokemonSelected?.base_experience"
      :height="pokemonSelected?.height"
      :img="pokemonSelected?.sprites.other.dream_world.front_default"
      :loading="loading"
      />
    </v-container>
    <v-container class="card-list">
      <v-text-field label="Procurar Pokemon" v-model="searchPokemonField"></v-text-field>
      <v-row no-gutters>
        <v-col v-for="pokemon in pokemonsFiltered" :key="pokemon.name" cols="12" sm="6">
          <div @click="selectPokemon(pokemon)" >
            <ListPokemons :name="pokemon.name"
            :imgUrl="imgUrlBase + pokemon.url.split('/')[6] + '.svg'"
            />
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script setup>
import CardPokemonSelected from '@/components/CardPokemonSelected.vue';
import ListPokemons from '@/components/ListPokemons.vue';
import { onMounted, reactive, ref, computed } from 'vue';
import { useDisplay } from 'vuetify'

const { mobile } = useDisplay({ mobileBreakpoint: 450 })

let imgUrlBase = ref("https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/")
let pokemons = reactive(ref())
let searchPokemonField = ref('')
let pokemonSelected = reactive(ref())
let loading = ref(false)

onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
    .then(res => res.json())
    .then(res => pokemons.value = res.results)
})

const pokemonsFiltered = computed(() => {
  if(pokemons.value && searchPokemonField.value)
    return pokemons.value.filter(pokemon => pokemon.name.toLowerCase().includes(searchPokemonField.value.toLowerCase()))

  return pokemons.value
})

const selectPokemon = async (pokemon) => {
  loading.value = true
  await fetch(pokemon.url)
  .then(res => res.json())
  .then(res => pokemonSelected.value = res)
  .catch(err => alert(err))
  .finally(() => loading.value = false)
}
</script>

<style lang="sass" scoped>
.card-list
  max-height: 85vh
  overflow-y: scroll
</style>