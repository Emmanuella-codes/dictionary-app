<script>
import SearchResults from '../components/SearchResults.vue'
import HomeCmp from '../components/HomeCmp.vue'
// import LoaderCmp from '../components/LoaderCmp.vue'
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
      dataResults: null,
      isLoading: false
    }
  },
  //check for new actions performed on the route param
  //used to trigger click on synonyms and antonyms
  watch: {
    '$route.params.word'(newValue) {
      if (newValue) {
        this.searchData(newValue)
      }
    }
  },
  created() {
    //check if the link has a param
    if (this.$route.params.word) {
      //pass the param word into the searchData function
      this.searchData(this.$route.params.word)
    }
  },
  methods: {
    searchData(searchWord) {
      axios
        .get(`https://api.dictionaryapi.dev/api/v2/entries/en/${searchWord}`)
        .then((res) => {
          this.dataResults = res.data
          this.isLoading = true
        })
        .catch((err) => {
          console.log(err)
        })
    },

    onWordClick(word) {
      this.$router.push(`/${word}`)
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
        <SearchResults :data="dataResults" @word-click="onWordClick" />
      </div>
    </div>
    <footer v-if="dataResults" class="mt-14 pb-5">
      <FooterCmp :data="dataResults" />
    </footer>
  </section>
</template>
