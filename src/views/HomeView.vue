<script>
import HomeCmp from '../components/HomeCmp.vue'

export default {
  components: {
    HomeCmp
  },
  props: ['data'],
  methods: {
    handleSearch(searchWord) {
      this.$router.push(`/${searchWord}`)
    }
  }
}
</script>

<template>
  <div class="w-full h-screen bg-white dark:bg-black">
    <div id="container" class="lg:mx-auto max-w-[90%] lg:w-[80%]">
      <HomeCmp @search="handleSearch" />
    </div>
  </div>
</template>
