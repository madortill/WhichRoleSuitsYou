<template>
  <div id="open-page">
    <p>איזה תפקיד הכי מתאים לך</p>
    <img
      class="bahad-symbol"
      src="/media/bahadEducation.png"
      alt="bahad-Education"
    />
    <img
      class="open-headline"
      src="\media\openHeadline.png"
      alt="open-headline"
    />

    <p class="start-btn" @click="startQuiz">התחל</p>
  </div>
</template>

<script>
export default {
  name: "open-page",

  components: {},
  props: [],
  data() {
    return {};
  },
  methods: {
    startQuiz() {
      this.$emit('start-quiz');
    },
  },
};
</script>

<style scoped>
#open-page {
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  flex-direction: column;
  color: #157145;
  font-size: 1.5rem;
  font-weight: bold;
}

.bahad-symbol {
  width: 15rem;
}

.open-headline {
  width: 30rem;
}

.start-btn {
  z-index: 1;
  width: 5rem;
  height: 3rem;
  font-size: 1rem;
  background-color: #2180c3;
  border-radius: 1.5rem;
  padding: 0;
  color: white;
  /* Centering the text */
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  transition: background-color 0.3s ease;
  cursor: pointer;
}

.start-btn:hover {
  background-color: #649dc5;
}
@media screen and (max-width: 480px) {
}
</style>
