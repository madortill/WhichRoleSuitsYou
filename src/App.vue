<template>
  <div id="app">
    <img
      v-if="pageNum > 0"
      class="mini-bahad-symbol"
      src="/media/bahadEducation.png"
      alt="bahad-Education"
    />

    <img v-if="showMadorTill" class="mador-till" src="/media/MadorTill/green.svg" alt="mador-till" />

    <open-page v-if="pageNum === 0" @start-intro="nextPage" />
    <intro @start-quiz="toQuiz" v-if="pageNum === 1" />
    <quiz :userGender="userGender" v-if="pageNum === 2" @show-result="showResult" @hide-mador-till-logo="hideMadorTillLogo"/>
    <result v-if="pageNum === 3" :resultIndex="resultIndex" :userName="userName"/>
  </div>
</template>

<script>
import OpenPage from "./components/OpenPage.vue";
import Quiz from "./components/Quiz.vue";
import Result from "./components/Result.vue";
import Intro from "./components/Intro.vue";

export default {
  name: "app",

  components: { OpenPage, Quiz, Result, Intro },
  props: [],
  data() {
    return {
      pageNum: 0,
      resultIndex: -1,
      userName: "",
      userGender: "",
      showMadorTill: true,
    };
  },
  methods: {
    showResult(i) {
      this.resultIndex = i;
      this.nextPage();
    },

    toQuiz(user) {
      this.userName = user.name;
      this.userGender = user.gender;
      this.nextPage();
    },

    nextPage() {
      this.pageNum++;
    },

    hideMadorTillLogo(){
      this.showMadorTill = false;
    }
  },
};
</script>

<style>
@font-face {
  font-family: "Assistant";
  src: url("@/assets/fonts/Assistant-Regular.ttf");
}
* {
  overflow: hidden;
  font-family: "Assistant";
  /* font-size: calc(10px + 0.5vw); */
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
  z-index: 1;
}

.mador-till {
  position: absolute;
  bottom: 1rem;
  right: 1rem;
  width: 4rem;
  z-index: 1;
}
@media screen and (max-width: 500px) {
  body {
    height: 91vh;
    overflow: hidden;
  }

  #app {
    height: 91vh;
  }
}
</style>
