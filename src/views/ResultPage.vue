<script setup>
import SearchResults from '../components/SearchResults.vue'

defineProps(['data'])
</script>

<template>
  <div id="result" class="lg:mx-auto max-w-[90%] lg:w-[80%]">
    <SearchResults :data="data" />
  </div>
</template>
