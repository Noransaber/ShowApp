<script setup>
import GameOfThronesSuspense from './components/GameOfThronesSuspense.vue'
import RickyandMorty from './components/RickyandMorty Card.vue'
import Hero from './components/Hero.vue'
import { ref } from "vue"

const isGameOfThrones = ref(true)
</script>

<template>
  
  <main>
    <Hero :isGameOfThrones='isGameOfThrones'
    @selcetedShow='isGameOfThrones = !isGameOfThrones'
    />
   <keep-alive>
   <Component :is='isGameOfThrones ?GameOfThronesSuspense : RickyandMorty ' />
   </keep-alive>
 
  </main>
</template>


