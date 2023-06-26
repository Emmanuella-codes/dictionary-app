<script setup>
defineProps(['data'])
</script>

<template>
  <div class="mb-6 text-gray-500 max-w-[75%] mx-auto" id="footer">
    <h4 class="italic text-gray-800 dark:text-slate-300 border-t-2 pt-3 text-lg">Source</h4>
    <ul class="pb-2">
      <li>
        <a :href="data[0].sourceUrls" target="_blank"
          ><span> https://en.wiktionary.org/wiki/{{ data[0].word }} </span></a
        >
      </li>
    </ul>
  </div>
</template>

<style scoped>
/* @media (max-width: 640px) {
  #footer-text p {
    width: 50%;
  }
}
*/
</style>
