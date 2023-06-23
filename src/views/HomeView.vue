<script>
import NavBar from '../components/NavBar.vue'
import ResultPage from './ResultPage.vue'
import axios from 'axios'

export default {
  components: {
    NavBar,
    ResultPage
  },
  data() {
    return {
      searchData: null,
      searchWord: ''
    }
  },
  methods: {
    handleSearch() {
      axios
        .get(`https://api.dictionaryapi.dev/api/v2/entries/en/${this.searchWord}`)
        .then((res) => {
          this.searchData = res.data
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
    <div id="container" class="lg:mx-auto max-w-[90%] lg:w-[80%]">
      <header class="">
        <NavBar />
      </header>
      <!--input field-->
      <main class="mt-14">
        <div
          class="flex justify-around max-w-[70%] lg:max-w-[50%] mx-auto focus:border-0 focus:border-transparent rounded-md"
        >
          <div class="group">
            <span class="sr-only">Search word</span>
            <input
              required
              v-model="searchWord"
              type="text"
              name="search"
              class="input dark:text-slate-100"
            />
            <span class="highlight"></span>
            <span class="bar"></span>
            <label class="dark:text-slate-100">Search for anything...</label>

            <button @click="handleSearch" class="">
              <svg xmlns="http://www.w3.org/2000/svg" width="48" height="48" viewBox="0 0 48 48">
                <g fill="none" stroke="#7f8487" stroke-linejoin="round" stroke-width="4">
                  <path
                    d="M21 38c9.389 0 17-7.611 17-17S30.389 4 21 4S4 11.611 4 21s7.611 17 17 17Z"
                  />
                  <path
                    stroke-linecap="round"
                    d="M26.657 14.343A7.975 7.975 0 0 0 21 12a7.975 7.975 0 0 0-5.657 2.343m17.879 18.879l8.485 8.485"
                  />
                </g>
              </svg>
            </button>
          </div>
        </div>
      </main>
    </div>
    <!--result section-->
    <section>
      <ResultPage v-if="searchData" :data="searchData" class="my-24" />
    </section>
  </div>
</template>

<style scoped>
.group {
  position: relative;
  width: 100%;
}

.input {
  font-size: 16px;
  padding: 10px 10px 10px 5px;
  display: block;
  width: 100%;
  border: none;
  border-bottom: 1px solid #515151;
  background: transparent;
}

.input:focus {
  outline: none;
}

label {
  color: #999;
  font-size: 18px;
  font-weight: normal;
  position: absolute;
  pointer-events: none;
  left: 5px;
  top: 10px;
  transition: 0.2s ease all;
  -moz-transition: 0.2s ease all;
  -webkit-transition: 0.2s ease all;
}

.input:focus ~ label,
.input:valid ~ label {
  top: -20px;
  font-size: 14px;
  color: #5264ae;
}

.bar {
  position: relative;
  display: block;
  width: 100%;
}

.bar:before,
.bar:after {
  content: '';
  height: 2px;
  width: 0;
  bottom: 1px;
  position: absolute;
  background: #5264ae;
  transition: 0.2s ease all;
  -moz-transition: 0.2s ease all;
  -webkit-transition: 0.2s ease all;
}

.bar:before {
  left: 50%;
}

.bar:after {
  right: 50%;
}

.input:focus ~ .bar:before,
.input:focus ~ .bar:after {
  width: 50%;
}

.highlight {
  position: absolute;
  height: 60%;
  width: 100px;
  top: 25%;
  left: 0;
  pointer-events: none;
  opacity: 0.5;
}

.input:focus ~ .highlight {
  animation: inputHighlighter 0.3s ease;
}

@keyframes inputHighlighter {
  from {
    background: #5264ae;
  }

  to {
    width: 0;
    background: transparent;
  }
}
</style>
