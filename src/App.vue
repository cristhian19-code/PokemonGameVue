<template>
<div class="min-h-screen transition-colors duration-500" :class="darkmode ? 'bg-gray-800 text-gray-300' : 'bg-white text-gray-700'">
  <div class="flex justify-end px-5 py-3">
    <button @click="darkmode = !darkmode" class="px-5 py-2 rounded-md" :class="!darkmode ? 'text-white bg-gray-800' : 'bg-white text-gray-800'">Dark</button>
  </div>
  <PokemonPage class="p-5" />
</div>
</template>

<script>
import PokemonPage from './pages/PokemonPage.vue'
export default {
  name: 'App',
  data() {
    return {
      darkmode: false
    }
  },
  components: {
    PokemonPage
  }
}
</script>

<style>
</style>
