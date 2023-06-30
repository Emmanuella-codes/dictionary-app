<script>
import SearchResults from '../components/SearchResults.vue'
import HomeCmp from '../components/HomeCmp.vue'
import FooterCmp from '../components/FooterCmp.vue'
import axios from 'axios'

export default {
  components: {
    SearchResults,
    HomeCmp,
    FooterCmp
  },
  data() {
    return {
      dataResults: null
    }
  },
  methods: {
    searchData(searchWord) {
      axios
        .get(`https://api.dictionaryapi.dev/api/v2/entries/en/${searchWord}`)
        .then((res) => {
          this.dataResults = res.data
          console.log(this.dataResults)
        })
        .catch((err) => {
          console.log(err)
        })
    }
  }
}
</script>

<template>
  <section class="bg-white dark:bg-black">
    <div id="result" class="lg:mx-auto max-w-[90%] mx-auto lg:w-[80%]">
      <!--search input-->
      <section>
        <HomeCmp @search="searchData" />
      </section>
      <div v-if="dataResults" class="bg-white dark:bg-black mt-9">
        <SearchResults :data="dataResults" />
      </div>
    </div>
    <footer v-if="dataResults" class="mt-14 pb-5">
      <FooterCmp :data="dataResults" />
    </footer>
  </section>
</template>
