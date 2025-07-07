<template>
  <div id="quiz">
    <div class="quiz-container" v-if="!isKickedOut">
      <p class="question">{{ questions[numQues].title }}</p>
      <div class="btns-container">
        <img
          class="btn"
          src="/media/noBtn.png"
          alt="no"
          @click="choseABtn(false)"
        />
        <img
          class="btn"
          src="/media/yesBtn.png"
          alt="yes"
          @click="choseABtn(true)"
        />
      </div>
    </div>
    <kicked-out v-if="isKickedOut" />
  </div>
</template>

<script>
import KickedOut from "./KickedOut.vue";
export default {
  name: "quiz",

  components: { KickedOut },
  props: [],
  data() {
    return {
      questions: [
        {
          title: "האם את/ה מעוניין/ת לשרת שירות משמעותי?",
          indexYesRoles: [],
          indexNoRoles: [],
        },
        {
          title: "האם את/ה אוהב/ת שטח?",
          indexYesRoles: [0, 1],
          indexNoRoles: [2, 3, 4, 5],
        },
        {
          title: "האם את/ה אוהב/ת לעבוד עם מחשבים?",
          indexYesRoles: [4],
          indexNoRoles: [0, 1, 2, 3, 5],
        },
        {
          title: "האם את/ה אוהב/ת את ההיסטוריה של הארץ?",
          indexYesRoles: [2],
          indexNoRoles: [0, 1, 3, 4, 5],
        },
        {
          title: "האם את/ה אוהב/ת לעבוד עם ילדים?",
          indexYesRoles: [5],
          indexNoRoles: [0, 1, 2, 3, 4],
        },
        {
          title: "האם את/ה אוהב/ת את השפה העברית?",
          indexYesRoles: [1, 3],
          indexNoRoles: [0, 2, 4, 5],
        },
        {
          title: 'האם את/ה מתעניינ/ת ביחידות השונות בצה"ל?',
          indexYesRoles: [0],
          indexNoRoles: [1, 2, 3, 4, 5],
        },
        {
          title: "האם את/ה אוהב/ת לעבוד עם בני נוער?",
          indexYesRoles: [0, 4, 5],
          indexNoRoles: [1, 2, 3],
        },
        {
          title: "האם את/ה אוהב/ת לעבוד בצוות?",
          indexYesRoles: [1],
          indexNoRoles: [0, 2, 3, 4, 5],
        },
        {
          title: "האם יש לך ניסיון עם אוכלוסיות ייחודיות?",
          indexYesRoles: [3],
          indexNoRoles: [1],
        },
      ],
      arrRoles: [
        {
          name: "מפקד/ת נוער",
          counter: 0,
        },
        {
          name: 'מפק"צ חינוך',
          counter: 0,
        },
        {
          name: 'מש"ק/ית חו"יה',
          counter: 0,
        },
        {
          name: 'מש"ק/ית הוראה והדרכה',
          counter: 0,
        },
        {
          name: 'מש"ק/ית גשרים',
          counter: 0,
        },
        {
          name: 'מש"ק/ית תקומה',
          counter: 0,
        },
      ],
      numQues: 0,
      isKickedOut: false,
    };
  },
  methods: {
    choseABtn(theBtn) {
      // אם שאלה ראשונה וענו לא
      if (this.numQues === 0 && !theBtn) {
        this.isKickedOut = true;
        return;
      } else if (this.numQues !== 0) {
        let arr;
        if (theBtn) {
          arr = this.questions[this.numQues].indexYesRoles;
        } else {
          arr = this.questions[this.numQues].indexNoRoles;
        }
        this.addCountAccordingToChoise(arr);
      }

      // קידום לשאלה הבאה
      if (this.numQues < 10) {
        this.numQues++;
      } else if (this.numQues === 10) {
        this.showResult();
      }
    },

    addCountAccordingToChoise(arr) {
      for (let i = 0; i < arr.length; i++) {
        this.arrRoles[arr[i]].counter++;
      }
    },

    checkWhichRoleBiggestCount() {
      let maxCounter = -1;
      let theRole = [];

      for (let i = 0; i < this.arrRoles.length; i++) {
        const count = this.arrRoles[i].counter;

        if (count > maxCounter) {
          maxCounter = count;
          theRole = [i]; // התוצאה החדשה הכי גבוהה – איפוס המערך
        } else if (count === maxCounter) {
          theRole.push(i); // תוצאה שווה לגבוהה – הוספה למערך
        }
      }

      return theRole;
    },

    showResult() {
      let resultArr = this.checkWhichRoleBiggestCount();
      if (resultArr.length > 0) {
        const randomIndex = Math.floor(Math.random() * resultArr.length);
        this.$emit("show-result", resultArr[randomIndex]);
      }
    },
  },
};
</script>

<style scoped>
#quiz {
  width: 100vw;
  height: 100vh;
  /* display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly; */
}

.quiz-container {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
}

.question {
  font-size: 2rem;
  font-weight: bold;
  margin-top: -8rem;
  animation: floatUpDown 3s ease-in-out infinite;
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
.btns-container {
  display: flex;
  align-items: center;
  width: 100vw;
  justify-content: space-evenly;
}

.btn {
  cursor: pointer;
  width: 9rem;
}
@media screen and (max-width: 480px) {
}
</style>
