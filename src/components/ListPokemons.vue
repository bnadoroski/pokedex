<template>
    <v-hover v-slot="{ isHovering, props }">
        <v-card class="cardItem mx-auto mt-3" max-width="344" :class="{ 'card': isHovering }" v-bind=props>
            <v-card-item class="d-flex align-center justify-center">
                
                <v-card-title class="text-center">
                    {{ pokemon.name }}
                </v-card-title>
                <v-divider color="info"></v-divider>
                <v-img class="animate__animated " contain height="250"
                    :class="{ 'animate__pulse': isHovering }" :width="250" :alt="pokemon.name"
                    :src="imgUrl" v-bind=props></v-img>
            </v-card-item>
        </v-card>
    </v-hover>
</template>

<script setup>
import 'animate.css'
import { defineProps } from 'vue';

const pokemon = defineProps(["name", "imgUrl"])
</script>

<style lang="sass" scoped>
.cardItem
    border: thin solid #c6c6c6
    cursor: pointer

.card
    background: radial-gradient(circle, rgba(63,67,251,0.5) 0%, rgba(70,252,219,0.4) 100%)
</style>