<template>
  <div id="app">
    <img
      v-if="pageNum === 1"
      class="mini-bahad-symbol"
      src="/media/bahadEducation.png"
      alt="bahad-Education"
    />

    <img class="mador-till" src="/media/MadorTill.svg" alt="mador-till" />
    
    <open-page v-if="pageNum === 0" @start-quiz="nextPage" />
    <quiz v-if="pageNum === 1" @show-result="nextPage"/>
    <result v-if="pageNum === 2"/>

  </div>
</template>

<script>
import OpenPage from "./components/OpenPage.vue";
import Quiz from "./components/Quiz.vue";
import Result from './components/Result.vue';

export default {
  name: "app",

  components: { OpenPage, Quiz, Result },
  props: [],
  data() {
    return {
      pageNum: 0,
    };
  },
  methods: {
    nextPage() {
      this.pageNum++;
    },
  },
};
</script>

<style>
* {
  overflow: hidden;
  font-family: "Assistant";
  font-size: calc(10px + 0.5vw);
}

:root {
  font-size: calc(10px + 0.5vw);
}

body {
  margin: 0;
  direction: rtl;
  background-color: #cfedf8;
  overflow: hidden;
  font-size: calc(10px + 0.5vw);
}

#app {
  font-family: "Heebo";
  width: 100vw;
  height: 100vh;
  position: relative;
  text-align: center;
  background-color: #cfedf8;
  font-size: 1.5rem;
}

.mini-bahad-symbol {
  width: 4rem;
  position: absolute;
  left: 1rem;
  top: 1rem;
}

.mador-till {
  position: absolute;
  bottom: 1rem;
  right: 1rem;
  width: 4rem;
}
@media screen and (max-width: 600px) {
  body {
    /* height: 91vh; */
    overflow: hidden;
  }

  /* #app {
    height: 91vh;
  } */
}
</style>
