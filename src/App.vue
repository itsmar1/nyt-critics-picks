<template>
  <the-header></the-header>
  <the-filters></the-filters>
  <h1 class="text-5xl text-center font-bold text-green-400 tracking-widest">Hello world</h1>
</template>

<script>


import TheHeader from './components/layout/TheHeader.vue'
import TheFilters from './components/layout/TheFilters.vue'

export default {
  name: 'App',
  components: {
    TheHeader,
    TheFilters
  }
}
</script>


