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
  <div>
    <label for="font-family"></label>
    <select
      id="font-family"
      v-model="selectedFont"
      @change="changeFontFamily"
      class="border shadow-sm border-slate-300 placeholder-slate-400 focus:outline-none focus:border-sky-500 focus:ring-sky-500 block w-full rounded-md sm:text-sm focus:ring-1 py-3 px-2"
    >
      <option value="serif">Serif</option>
      <option value="sans-serif">Sans-serif</option>
      <option value="cursive">Cursive</option>
      <option value="fantasy">Fantasy</option>
      <option value="monospace">Monospace</option>
    </select>
  </div>
</template>
