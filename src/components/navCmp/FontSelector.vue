<script>
export default {
  data() {
    return {
      selectedFont: 'serif'
    }
  },
  methods: {
    changeFontFamily() {
      document.documentElement.style.fontFamily = this.selectedFont
    }
  }
}
</script>

<template>
  <label
    for="countries"
    class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
  ></label>
  <select
    id="font-family"
    v-model="selectedFont"
    @change="changeFontFamily"
    class="bg-white dark:bg-black border-r-2 border-gray-300 text-gray-900 text-sm focus:ring-blue-500 focus:border-blue-500 block p-1 w-16 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 lg:text-lg"
  >
    <option selected value="serif">Serif</option>
    <option value="sans-serif">Sans-serif</option>
    <option value="cursive">Cursive</option>
    <option value="fantasy">Fantasy</option>
    <option value="monospace">Monospace</option>
  </select>
</template>
