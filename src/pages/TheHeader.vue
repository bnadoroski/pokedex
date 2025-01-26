<template>
  <v-card>
    <v-layout>
      <v-app-bar
        color="blue"
        absolute
      >        
        <v-app-bar-title @click="changeTab">
          <router-link to="/home" class="centralizar-logo">
            <img cover :width="40" src="https://cdn-icons-png.flaticon.com/512/188/188987.png" alt="">
            <span>Pokedex</span> 
          </router-link>
        </v-app-bar-title>

        <template v-slot:extension>
          <v-tabs
            v-model="tab"
            align-tabs="title"
          >
          
            <v-tab :value="0">
              <router-link to="/home">Home</router-link>
            </v-tab>

          </v-tabs>
        </template>
      </v-app-bar>

      <v-main>
        <router-view />
      </v-main>

    </v-layout>
  </v-card>
</template>

<script setup>
import {ref} from 'vue'
const tab = ref(0)

function changeTab() {
  console.log(tab)
  tab.value = 0
}
</script>

<style lang="sass" scoped>
a
  text-decoration: none
  color: #fff

.centralizar-logo
  display: flex
  align-items: center
  gap: 1rem
</style>