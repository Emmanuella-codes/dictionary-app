<script setup>
defineProps(['data'])

const playAudio = (sound) => {
  if (sound) {
    const audio = new Audio(sound)
    audio.play()
  }
}
</script>

<template>
  <div id="content-container" class="h-screen w-full">
    <h1 class="text-center text-lg text-[#a58edb]">Search results for : {{ data[0].word }}</h1>
    <!--search result from api-->
    <div class="max-w-[90%] mx-auto">
      <!--word and audio-->
      <div class="flex justify-between my-14" id="search-header">
        <div id="word">
          <h2 id="boldWord" class="lg:text-5xl text-4xl font-semibold dark:text-slate-100">
            {{ data[0].word }}
          </h2>
          <h3 id="italicWord" class="lg:text-2xl text-xl lg:pt-3 text-[#aa8eeb]">
            {{ data[0].phonetic }}
          </h3>
        </div>
        <div id="audio-btn">
          <button @click="playAudio(`${data[0].phonetics[0].audio}`)"></button>
        </div>
      </div>
      <!--main content-->
      <div>
        <!--part of speech and hr-->
        <div class="flex items-center gap-3">
          <p class="lg:text-3xl text-xl font-semibold italic dark:text-slate-200">
            {{ data[0].meanings[0].partOfSpeech }}
          </p>
          <span class="border-b-4 w-full pt-1 lg:pt-2"></span>
        </div>

        <div id="first-meaning" class="mt-3">
          <h3 class="text-xl">Meaning</h3>
          <ul class="space-y-1 text-gray-500 list-disc list-inside dark:text-gray-400">
            <li v-for="def in data[0].meanings[0].definitions.slice(0, 3)" :key="def">
              {{ def.definition }}
            </li>
          </ul>
          <div class="mt-2" v-if="data[0].meanings[0].definitions.example">
            <span class="border-l-4"></span>
            <p>{{ data[0].meanings[0].definitions.example }}</p>
          </div>
          <!--synonyms-->
          <div class="mt-4" v-if="data[0].meanings[0].synonyms">
            <h4 class="italic dark:text-slate-200">Synonyms</h4>
            <ul class="flex flex-row gap-3">
              <li
                v-for="synonym in data[0].meanings[0].synonyms"
                :key="synonym"
                class="text-[#aa8eeb]"
              >
                {{ synonym }}
              </li>
            </ul>
          </div>
          <!--antonyms-->
          <div class="mt-4" v-if="data[0].meanings[0].antonyms.length > 0">
            <h4 class="italic">Antonyms</h4>
            <ul>
              <li v-for="antonym in data[0].meanings[0].antonyms" :key="antonym">
                {{ antonym }}
              </li>
            </ul>
          </div>
        </div>
      </div>
      <!--second meaning and definition-->
      <div class="mt-9" v-if="data[0].meanings[2]">
        <!--part of speech and hr-->
        <div class="flex items-center gap-3">
          <p class="lg:text-3xl text-xl font-semibold italic dark:text-slate-200">
            {{ data[0].meanings[1].partOfSpeech }}
          </p>
          <span class="border-b-4 w-full pt-1 lg:pt-2"></span>
        </div>

        <div id="first-meaning" class="mt-3">
          <h3 class="text-xl">Meaning</h3>
          <ul class="space-y-1 text-gray-500 list-disc list-inside dark:text-gray-400">
            <li v-for="def in data[0].meanings[1].definitions.slice(0, 3)" :key="def">
              {{ def.definition }}
            </li>
          </ul>
          <div class="mt-2" v-if="data[0].meanings[1].definitions.example">
            <span class="border-l-4"></span>
            <p>{{ data[0].meanings[1].definitions.example }}</p>
          </div>
          <!--synonyms-->
          <div class="mt-4" v-if="data[0].meanings[1].definitions[0].synonyms.length > 0">
            <h4 class="italic">Synonyms</h4>
            <ul class="flex flex-row">
              <li v-for="synonym in data[0].meanings[1].definitions[0].synonyms" :key="synonym">
                {{ synonym }}
              </li>
            </ul>
          </div>
          <!--antonyms-->
          <div class="mt-4" v-if="data[0].meanings[1].definitions[0].antonyms.length > 0">
            <h4 class="italic">Antonyms</h4>
            <ul>
              <li v-for="antonym in data[0].meanings[1].definitions[0].antonyms" :key="antonym">
                {{ antonym }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
button {
  padding: 5px;
  border-radius: 100%;
  box-shadow: 0px 0px 5px 7px #c7b3f5;
  background-color: #ab92e4;
  color: white;
  font-size: 17px;
  border: none;
  display: flex;
  align-items: center;
}

button::before {
  content: 'fac';
  background-image: url('data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB3aWR0aD0iNzUycHQiIGhlaWdodD0iNzUycHQiIHZlcnNpb249IjEuMSIgdmlld0JveD0iMCAwIDc1MiA3NTIiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CiA8cGF0aCBkPSJtNTQ4Ljg2IDM4Mi4xNmMwIDM1LjUyLTMuMzE2NCA3MC4wOS05LjQ3MjcgMTAzLjI0LTAuOTQ1MzEgNC43MzQ0LTQuNzM0NCA3LjU3ODEtOS40NzI3IDcuNTc4MWgtMS44OTQ1Yy01LjIxMDktMC45NDUzMS04LjUyMzQtNi4xNTYyLTcuNTc4MS0xMC44OTEgNi4xNTYyLTMyLjIwMyA5LjQ3MjctNjUuODI4IDkuNDcyNy05OS45MjZzLTMuMzE2NC02OC42NjgtOS40NzI3LTEwMi43N2MtMC45NDUzMS01LjIxMDkgMi4zNjcyLTkuOTQ1MyA3LjU3ODEtMTAuODkxIDUuMjEwOS0wLjk0NTMxIDkuOTQ1MyAyLjM2NzIgMTAuODkxIDcuNTc4MSA2LjYzMjggMzUuMDM5IDkuOTQ5MiA3MC41NTkgOS45NDkyIDEwNi4wN3ptLTE0NC45Mi0xMzguNzZjMTAuODkxIDQ1LjkzOCAxNi41NzQgOTIuMzQ4IDE2LjU3NCAxMzguMjkgMCA0NS40NjUtNS4yMTA5IDg5Ljk4LTE2LjEwMiAxMzIuMTMtMC45NDUzMSAzLjMxNjQtMi4zNjcyIDYuMTU2Mi00LjI2MTcgOC41MjM0LTMuNzg5MSA1LjIxMDktOS40NzI3IDguMDUwOC0xNS42MjkgOC45OTYxaC0yLjgzOThjLTUuMjEwOSAwLTEwLjQxOC0xLjg5NDUtMTQuMjA3LTQuNzM0NGwtNzIuOTMtNTUuNDA2Yy0wLjk0NTMxLTAuNDcyNjYtMS44OTQ1LTAuOTQ1MzEtMi44Mzk4LTAuOTQ1MzFoLTUyLjA5NGMtOC41MjM0IDAtMTYuMTAyLTQuNzM0NC0yMC4zNjMtMTEuODQtMTIuMzEyLTIwLjgzNi0xOC40NjktNDYuODgzLTE4LjQ2OS03Ni4yNDYgMC0yOS44MzYgNi4xNTYyLTU3LjMwNSAxOC40NjktODEuOTMgMy43ODkxLTguMDUwOCAxMi4zMTItMTMuMjYyIDIxLjMxMi0xMy4yNjJoNTEuNjIxYzAuOTQ1MzEgMCAxLjg5NDUtMC40NzI2NiAyLjgzOTgtMC45NDUzMWw3MS41MDgtNTUuODg3YzIuODM5OC0xLjg5NDUgNS42ODM2LTMuMzE2NCA4Ljk5NjEtNC4yNjE3IDYuMTU2Mi0xLjQyMTkgMTIuMzEyLTAuNDcyNjYgMTcuOTk2IDIuODM5OCA1LjIxMDkgMy4zMTY0IDkgOC41MjczIDEwLjQxOCAxNC42ODR6bS0yLjgzOTggMTM4Ljc2YzAtNDQuNTE2LTUuMjEwOS04OS41MDgtMTUuNjI5LTEzNC4wMi0wLjQ3MjY2LTEuODk0NS0xLjQyMTktMi4zNjcyLTEuODk0NS0yLjgzOTgtMC40NzI2Ni0wLjQ3MjY2LTEuODk0NS0wLjk0NTMxLTMuNzg5MS0wLjQ3MjY2LTAuNDcyNjYgMC0xLjQyMTkgMC40NzI2Ni0xLjg5NDUgMC45NDUzMWwtNzEuNTA4IDU0LjkzOGMtNC4yNjE3IDMuMzE2NC05LjQ3MjcgNC43MzQ0LTE0LjY4IDQuNzM0NGgtNTEuMTQ4Yy0xLjg5NDUgMC0zLjMxNjQgMC45NDUzMS00LjI2MTcgMi44Mzk4LTEwLjg5MSAyMi4yNTgtMTYuNTc0IDQ2Ljg4My0xNi41NzQgNzMuODc5IDAgMjYuMDQ3IDUuMjEwOSA0OC43NzcgMTUuNjI5IDY2Ljc3MyAwLjk0NTMxIDEuNDIxOSAyLjM2NzIgMi4zNjcyIDQuMjYxNyAyLjM2NzJoNTIuMDk0YzUuMjEwOSAwIDEwLjQxOCAxLjg5NDUgMTQuNjggNC43MzQ0bDcxLjk4NCA1NS44ODNjMS40MjE5IDAuOTQ1MzEgMi44Mzk4IDAuOTQ1MzEgMy4zMTY0IDAuOTQ1MzEgMC45NDUzMSAwIDEuODk0NS0wLjQ3MjY2IDMuMzE2NC0xLjg5NDUgMC40NzI2Ni0wLjQ3MjY2IDAuNDcyNjYtMC45NDUzMSAwLjk0NTMxLTEuODk0NSA5Ljk0MTQtNDAuMjQ2IDE1LjE1Mi04My4zNDQgMTUuMTUyLTEyNi45MXptODIuODc1LTc5LjA4NmMtNS4yMTA5IDAuNDcyNjYtOC45OTYxIDUuMjEwOS04LjA1MDggMTAuNDE4IDIuODM5OCAyMi43MyA0LjI2MTcgNDUuOTM4IDQuMjYxNyA2OC42NjhzLTEuNDIxOSA0NS40NjUtNC4yNjE3IDY3LjI1Yy0wLjQ3MjY2IDUuMjEwOSAyLjgzOTggOS45NDUzIDguMDUwOCAxMC40MThoMS40MjE5YzQuNzM0NCAwIDguOTk2MS0zLjMxNjQgOS40NzI3LTguNTIzNCAyLjgzOTgtMjIuNzMgNC4yNjE3LTQ1LjkzOCA0LjI2MTctNjkuNjE3IDAtMjMuNjgtMS40MjE5LTQ3LjM1OS00LjI2MTctNzAuNTYyLTAuOTQ5MjItNS4yMTA5LTUuNjgzNi05LTEwLjg5NS04LjA1MDh6IiBmaWxsPSIjZmZmIi8+Cjwvc3ZnPgo=');
  background-size: 100%;
  background-repeat: no-repeat;
  color: transparent;
  position: relative;
  width: 50px;
  height: 50px;
  display: block;
}

button:active {
  border-radius: 100%;
  box-shadow: inset 0px 0px 10px 0px rgb(240, 237, 237);
}
</style>
