<script>
import SearchResults from '../components/SearchResults.vue'
import HomeCmp from '../components/HomeCmp.vue'
import axios from 'axios'

export default {
  components: {
    SearchResults,
    HomeCmp
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
          console.log(this.searchData)
        })
        .catch((err) => {
          console.log(err)
        })
    }
  }
}
</script>

<template>
  <div class="w-full h-screen bg-white dark:bg-black">
    <div id="result" class="lg:mx-auto max-w-[90%] mx-auto lg:w-[80%] bg-white dark:bg-black">
      <!--search input-->
      <div>
        <HomeCmp @search="searchData" />
      </div>
      <SearchResults :data="dataResults" />
    </div>
  </div>
</template>
