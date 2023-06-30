<script setup>
/* import { useDark, useToggle } from '@vueuse/core' */
import FontSelector from './navCmp/FontSelector.vue'
import ToggleBtn from './navCmp/ToggleBtn.vue'
</script>

<template>
  <nav id="navbar">
    <div class="flex flex-row items-center justify-between">
      <!--logo-->
      <div class="flex justify-start">
        <img src="../assets/da-logo.png" class="w-full lg:w-2/4" alt="logo" />
      </div>
      <!--div container for fonts and color toggle-->
      <div class="flex gap-3 lg:gap-6 items-center">
        <FontSelector />
        <ToggleBtn />
      </div>
    </div>
  </nav>
</template>
