<template>
    <div>
        <v-card class="mx-auto card pt-2 " max-width="500" :class="loading ? '' : 'animate__animated animate__flipInY'">
            <v-img v-if="pokemon.name" height="300" :src="pokemon.img" contain :alt="pokemon.name"></v-img>
            <v-img v-else height="300" src="../assets/egg_pokemon.svg" contain alt="???"></v-img>
            <v-card-title>
                {{ pokemon.name || '???' }}
            </v-card-title>

            <v-divider></v-divider>

            <v-card-text>
                <div class="d-flex justify-space-between py-3">
                    <section>
                        <v-card-subtitle>
                            <strong>XP: </strong>
                            <span>{{ pokemon.xp || '???' }}</span>
                        </v-card-subtitle>
                    </section>
                    <section>
                        <v-card-subtitle>
                            <strong>Altura: </strong>
                            <span>{{ pokemon.height || '???' }}</span>
                        </v-card-subtitle>
                    </section>
                </div>
            </v-card-text>
        </v-card>
    </div>
</template>

<script setup>
import 'animate.css'
import { defineProps } from 'vue';
const pokemon = defineProps(["name", "xp", "height", "img", "loading"])

</script>

<style lang="sass" scoped>
.card
    background: radial-gradient(circle, rgba(63,67,251,0.5) 0%, rgba(70,252,219,0.4) 100%)
    border: thin solid #c6c6c6
</style>