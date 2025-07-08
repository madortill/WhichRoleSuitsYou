<template>
  <div id="intro">
    <div class="card">
      <p class="headline blue-text">לפני שנתחיל</p>
      <p>בפניך יהיו 17 שאלות שתענה עליהם ב-</p>

      <div class="hearts-container">
        <img class="heart" src="/media/yesBtn.png" alt="yes" />
        <img class="heart" src="/media/noBtn.png" alt="no" />
      </div>
      <p>כדי לדעת מה התפקיד שמותאם לך</p>

      <div class="input-name-container">
        <p class="blue-text">מה השם שלך?</p>
        <input
          class="input-tag"
          placeholder="הקלידו כאן שם"
          v-model="fullName"
          @input="validateName"
          lang="he"
          type="text"
        />
      </div>

      <div class="input-gender-container blue-text">
        <p>תפנו אליי ב:</p>
        <div class="input-gender">
          <input
            type="radio"
            id="male"
            value="male"
            v-model="gender"
            class="the-checkbox"
          />
          <label for="male">זכר</label>
        </div>
        <div class="input-gender">
          <input
            type="radio"
            id="female"
            value="female"
            v-model="gender"
            class="the-checkbox"
          />
          <label for="female">נקבה</label>
        </div>
      </div>

      <p class="start-btn" :class="{ disabled: !canStart }" @click="startQuiz">
        התחל
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "intro",
  data() {
    return {
      fullName: "",
      gender: "",
      isNameValid: false,
    };
  },
  computed: {
    canStart() {
      return this.isNameValid && this.gender !== "";
    },
  },
  methods: {
    validateName() {
      const trimmed = this.fullName.trim();
      const regex = /^[A-Za-z\u0590-\u05FF\s]+$/;

      if (trimmed && !regex.test(trimmed)) {
        alert("נא להזין רק אותיות. מספרים ותווים מיוחדים אינם מותרים.");
        this.isNameValid = false;
        return;
      }

      if (trimmed.length < 2) {
        this.isNameValid = false;
        return;
      }

      this.isNameValid = true;
    },
    tryStartQuiz() {
      if (this.canStart) {
        this.startQuiz();
      }
    },
    startQuiz() {
      if (this.canStart) {
        this.$emit("start-quiz", {
          name: this.fullName.trim(),
          gender: this.gender,
        });
      }
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
  box-shadow: 0 -1rem 1rem rgba(0, 0, 0, 0.05);
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
  width: 5rem;
  height: 3rem;
  font-size: 1rem;
  background-color: #2180c3;
  border-radius: 1.5rem;
  color: white;
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

/* כשהכפתור "מושבת" */
.start-btn.disabled {
  background-color: gray;
  cursor: not-allowed;
  opacity: 0.6;
  pointer-events: none; /* מונע לחיצה בפועל */
}

.start-btn.disabled:hover {
  background-color: gray; /* ביטול hover */
}

.input-tag {
  border: 0.2rem solid #2180c3;
  border-radius: 2rem;
  width: 14rem;
  height: 3rem;
}

.input-name-container {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  width: 22rem;
}

.heart {
  width: 4rem;
}

.hearts-container {
  display: flex;
  width: 15rem;
  align-items: center;
  justify-content: space-evenly;
  margin-top: -2rem;
  margin-bottom: -2rem;
}

.headline {
  font-size: 2rem;
  margin-bottom: 0rem;
}

.blue-text {
  color: #2180c3;
}

.input-gender-container {
  display: flex;
  width: 20rem;
  justify-content: space-evenly;
}

.input-gender {
  display: flex;
  align-items: center;
}
@media screen and (max-width: 500px) {
  #intro {
    height: 91vh;
  }
}
</style>
