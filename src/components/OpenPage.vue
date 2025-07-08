<template>
  <div id="open-page">
    <lomda-info/>
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
    <p class="fix-size">בואו נמצא את התפקיד שהכי</p>
    <p class="fix-size-second">מתאים לכם</p>


    <p class="start-btn" @click="startQuiz">כן!</p>
  </div>
</template>

<script>
import LomdaInfo from './lomdaInfo.vue';
export default {
  name: "open-page",

  components: {LomdaInfo},
  props: [],
  data() {
    return {};
  },
  methods: {
    startQuiz() {
      this.$emit("start-intro");
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
  width: 9rem;
  filter: drop-shadow(0 0 1rem white);
  animation: floatUpDown 3s ease-in-out infinite;
}

@keyframes floatUpDown {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
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

.fix-size {
  font-size: 1.5rem;
}

.fix-size-second {
  font-size: 2rem;
  margin-top: -2rem;
}

@media screen and (max-width: 500px) {
  #open-page {
    height: 91vh;
  }
}
</style>
