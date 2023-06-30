<script>
import HomeCmp from '../components/HomeCmp.vue'
import LoaderCmp from '../components/LoaderCmp.vue'

export default {
  components: {
    HomeCmp,
    LoaderCmp
  },
  props: ['data'],
  data() {
    return {
      isLoading: false
    }
  },
  methods: {
    handleSearch(searchWord) {
      this.isLoading = true

      this.$router.push(`/${searchWord}`)
    }
  }
}
</script>

<template>
  <div class="w-full h-screen bg-white dark:bg-black">
    <div id="container" class="lg:mx-auto max-w-[90%] lg:w-[80%]">
      <HomeCmp @search="handleSearch" />
      <!--display loader if isLoading is true-->
      <LoaderCmp v-if="isLoading" />
    </div>
  </div>
</template>
