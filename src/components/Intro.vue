<template>
  <div id="open-page">
    <div class="card">
      <div>
        <p class="text-next-to-input">מה השם שלך?</p>
        <input
          class="input-tag"
          placeholder="הקלידו כאן שם"
          v-model="fullName"
          lang="he"
          type="text"
        />
      </div>

      <p class="start-btn" @click="startQuiz">התחל</p>
    </div>
  </div>
</template>

<script>
import LomdaInfo from "./lomdaInfo.vue";
export default {
  name: "open-page",

  components: { LomdaInfo },
  props: [],
  data() {
    return {};
  },
  methods: {
    startQuiz() {
      this.$emit("start-quiz");
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

.card {
  background-color: white;
  border-radius: 3rem;
  box-shadow: 0 -1rem 3rem rgba(0, 0, 0, 0.5);
  width: 100vh;
  height: 90%;
  position: absolute;
  bottom: 0;
}

@keyframes floatUpDown {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
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

.text-next-to-input {
    color: #2180c3;
}

.input-tag {
    border: 0.5rem solid #2180c3;
}

@media screen and (max-width: 500px) {
  #open-page {
    height: 91vh;
  }
}
</style>
