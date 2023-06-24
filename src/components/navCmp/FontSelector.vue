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
    class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
  >
    <option selected value="serif">Serif</option>
    <option value="sans-serif">Sans-serif</option>
    <option value="cursive">Cursive</option>
    <option value="fantasy">Fantasy</option>
    <option value="monospace">Monospace</option>
  </select>

  <!-- <div>
    <label for="font-family"></label>
    <select
      
      class="border-r lg:text-lg bg-transparent dark:text-gray-300 dark:bg-[#312846] border-slate-300 placeholder-slate-400 focus:outline-none focus:border-sky-500 focus:ring-sky-500 block w-full sm:text-sm focus:ring-1 py-3"
    >
      <option value="serif"></option>
      <option </option>
      <option </option>
      <option </option>
      <option </option>
    </select>
  </div> -->
</template>
