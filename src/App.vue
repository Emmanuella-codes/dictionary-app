<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>
<template>
  <div class="">
    <RouterLink to="/" />
    <RouterLink to="/:word" />
  </div>
  <RouterView></RouterView>
</template>

<style scoped></style>
