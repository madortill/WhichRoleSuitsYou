<template>
  <div id="intro">
    <div class="card">
      <p class="headline">לפני שנתחיל</p>
      <p>בפניך יהיו 10 שאלות שתענה עליהם ב-</p>

      <div class="hearts-container">
        <img class="heart" src="/media/yesBtn.png" alt="yes" />
        <img class="heart" src="/media/noBtn.png" alt="no" />
      </div>
      <p>כדי לדעת מה התפקיד שמותאם לך</p>
      <div class="input-container">
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
  name: "intro",

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
#intro {
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
  box-shadow: 0 -1rem 1rem rgba(0, 0, 0, 0.15);
  width: 100vw;
  height: 85%;
  position: absolute;
  /* bottom: -2rem; */
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  flex-direction: column;
  animation: slideIn 2s ease-in-out forwards;
}

@keyframes slideIn {
  from {
    bottom: -100rem;
  }
  to {
    bottom: -2rem;
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
  border: 0.2rem solid #2180c3;
  border-radius: 2rem;
  width: 14rem;
  height: 3rem;
}

.input-container {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  width: 22rem;
}

.heart {
  width: 5rem;
}

.hearts-container {
  display: flex;
  width: 15rem;
  align-items: center;
  justify-content: space-evenly;
}

.headline {
  color: #2180c3;
  font-size: 2rem;
  margin-bottom: -3rem;
}

@media screen and (max-width: 500px) {
  #intro {
    height: 91vh;
  }
}
</style>
