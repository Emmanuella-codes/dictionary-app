<script setup>
import SearchResults from '../components/SearchResults.vue'

defineProps(['data'])
</script>

<template>
  <div
    id="result"
    class="lg:mx-auto max-w-[90%] mx-auto lg:w-[80%] bg-white dark:bg-black"
  >
    <SearchResults :data="data" />
  </div>
</template>
