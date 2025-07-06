<template>
    <div id="app">
    <open-page @start-quiz="startQuiz"/>
    </div>
</template>

<script>
import OpenPage from './components/OpenPage.vue';

export default {
  name: "app",

  components: {OpenPage  },
  props: [
  
  ],
  data() {
    return {
    
    };
  },
  methods: {
    startQuiz() {

    },
      }
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
  background-color: #CFEDF8;
  overflow: hidden;
  font-size: calc(10px + 0.5vw);
}

#app {
  font-family: "Heebo";
  width: 100vw;
  height: 100vh;
  position: relative;
  text-align: center;
  background-color: #CFEDF8;
  font-size: 1.2rem;
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
