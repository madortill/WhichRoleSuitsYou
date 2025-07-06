<template>
  <div id="app">
    <img
     v-if="pageNum === 1"
      class="mini-bahad-symbol"
      src="/media/bahadEducation.png"
      alt="bahad-Education"
    />
    <open-page v-if="pageNum === 0" @start-quiz="startQuiz" />
    <quiz  v-if="pageNum === 1"/>
  </div>
</template>

<script>
import OpenPage from "./components/OpenPage.vue";
import Quiz from './components/Quiz.vue';

export default {
  name: "app",

  components: { OpenPage, Quiz },
  props: [],
  data() {
    return {
      pageNum: 0,
    };
  },
  methods: {
    startQuiz() {
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
  font-size: 1.2rem;
}

.mini-bahad-symbol {
  width: 4rem;
  position: absolute;
  left: 1rem;
  top: 1rem;
}

@media (min-width: 1024px) {
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
