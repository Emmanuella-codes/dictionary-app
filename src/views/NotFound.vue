<script>
import ErrorCmp from '../components/ErrorCmp.vue'

export default {
  components: {
    ErrorCmp
  },
  
}
</script>

<template>
  <section class="bg-white dark:bg-black w-full h-screen">
    <div id="result" class="lg:mx-auto max-w-[90%] mx-auto lg:w-[80%]">
      <ErrorCmp :data="errorData" />
    </div>
  </section>
</template>
