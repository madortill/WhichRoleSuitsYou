<template>
  <div id="quiz">
    <div class="quiz-container" v-if="!isKickedOut">
      <div class="num-ques-container">
        <p>{{ this.numQues + 1 }}</p>
      </div>
      <div class="dots-container up">
        <img class="dots" src="/media/upDots.png" />
      </div>
      <p class="question">{{ questions[numQues][userGender + "Title"] }}</p>
      <div class="dots-container down">
        <img class="dots" src="/media/downDots.png" />
      </div>
      <div class="btns-container">
        <div class="btn-container">
          <img
            class="btn"
            :class="{ 'clicked-heart': clickedNo }"
            src="/media/noBtn.png"
            alt="no"
            @click="choseABtn(false)"
          />
        </div>
        <div class="btn-container">
          <img
            class="btn"
            :class="{ 'clicked-heart': clickedYes }"
            src="/media/yesBtn.png"
            alt="yes"
            @click="choseABtn(true)"
          />
        </div>
      </div>

      <div class="soldier-container">
        <div class="talk-bubble">{{ goodWordArr[goodWordNum] }}</div>
        <img class="soldier" src="/media/soldier/quiz.png" alt="soldier" />
      </div>
    </div>
    <kicked-out v-if="isKickedOut" :userGender="userGender" />
  </div>
</template>

<script>
import KickedOut from "./KickedOut.vue";
export default {
  name: "quiz",

  components: { KickedOut },
  props: ["userGender"],
  data() {
    return {
      questions: [
        {
          maleTitle: "האם אתה מעוניין לשרת שירות משמעותי?",
          femaleTitle: "האם את מעוניינת לשרת שירות משמעותי?",
          indexYesRoles: [],
          indexNoRoles: [],
        },
        {
          maleTitle: "האם אתה אוהב שטח?",
          femaleTitle: "האם את אוהבת שטח?",
          indexYesRoles: [0, 1],
          indexNoRoles: [2, 3, 4, 5],
        },
        {
          maleTitle: "האם אתה אוהב לעבוד עם מחשבים?",
          femaleTitle: "האם את אוהבת לעבוד עם מחשבים?",
          indexYesRoles: [4],
          indexNoRoles: [0, 1, 2, 3, 5],
        },
        {
          maleTitle: "האם אתה אוהב את ההיסטוריה של הארץ?",
          femaleTitle: "האם את אוהבת את ההיסטוריה של הארץ?",
          indexYesRoles: [2],
          indexNoRoles: [0, 1, 3, 4, 5],
        },
        {
          maleTitle: "האם אתה אוהב לעבוד עם ילדים?",
          femaleTitle: "האם את אוהבת לעבוד עם ילדים?",
          indexYesRoles: [5],
          indexNoRoles: [0, 1, 2, 3, 4],
        },
        {
          maleTitle: "האם אתה אוהב את השפה העברית?",
          femaleTitle: "האם את אוהבת את השפה העברית?",
          indexYesRoles: [1, 3],
          indexNoRoles: [0, 2, 4, 5],
        },
        {
          maleTitle: 'האם אתה מתעניין ביחידות השונות בצה"ל?',
          femaleTitle: 'האם את מתעניינת ביחידות השונות בצה"ל?',
          indexYesRoles: [0],
          indexNoRoles: [1, 2, 3, 4, 5],
        },
        {
          maleTitle: "האם אתה אוהב לעבוד עם בני נוער?",
          femaleTitle: "האם את אוהבת לעבוד עם בני נוער?",
          indexYesRoles: [0, 4, 5],
          indexNoRoles: [1, 2, 3],
        },
        {
          maleTitle: "האם אתה אוהב לעבוד בצוות?",
          femaleTitle: "האם את אוהבת לעבוד בצוות?",
          indexYesRoles: [1],
          indexNoRoles: [0, 2, 3, 4, 5],
        },
        {
          maleTitle: "האם יש לך ניסיון עם אוכלוסיות ייחודיות?",
          femaleTitle: "האם יש לך ניסיון עם אוכלוסיות ייחודיות?",
          indexYesRoles: [3],
          indexNoRoles: [1],
        },
        {
          maleTitle: "יש לך ניסיון הדרכתי?",
          femaleTitle: "יש לך ניסיון הדרכתי?",
          indexYesRoles: [0, 1, 3],
          indexNoRoles: [2, 4, 5],
        },
        {
          maleTitle: "האם חשוב לך לשקם את העוטף הצפוני והדרומי?",
          femaleTitle: "האם חשוב לך לשקם את העוטף הצפוני והדרומי?",
          indexYesRoles: [5],
          indexNoRoles: [0, 1, 2, 3, 4],
        },
        {
          maleTitle: "האם בעינייך ידע הוא הכלי לשינוי חברתי?",
          femaleTitle: "האם בעינייך ידע הוא הכלי לשינוי חברתי?",
          indexYesRoles: [4],
          indexNoRoles: [0, 1, 2, 3, 5],
        },
        {
          maleTitle: "האם אתה מאלה שמארגנים הכל מבין החברים שלך?",
          femaleTitle: "האם את מאלה שמארגנים הכל מבין החברים שלך?",
          indexYesRoles: [2],
          indexNoRoles: [0, 1, 3, 4, 5],
        },
        {
          maleTitle: "האם לדעתך יש לך חוסן גבוה?",
          femaleTitle: "האם לדעתך יש לך חוסן גבוה?",
          indexYesRoles: [0, 1],
          indexNoRoles: [2, 3, 4, 5],
        },
        {
          maleTitle: 'האם אתה חושב שחינוך בצה"ל הוא דבר הכרחי?',
          femaleTitle: 'האם את חושבת שחינוך בצה"ל הוא דבר הכרחי?',
          indexYesRoles: [],
          indexNoRoles: [],
        },
        {
          maleTitle: "האם אתה אוהב להתעסק במספרים?",
          femaleTitle: "האם את אוהבת להתעסק במספרים?",
          indexYesRoles: [4],
          indexNoRoles: [0, 1, 2, 3, 5],
        },
      ],
      arrRoles: [0, 0, 0, 0, 0, 0],
      numQues: 0,
      isKickedOut: false,
      goodWordArr: [
        "מעניין אם יצא לך כמוני",
        "בחירה טובה",
        "אין על חיל חינוך",
        "כל הכבוד עוד קצת!",
        "יאללה תחליטו!!",
      ],
      goodWordNum: 0,
      clickedYes: false,
      clickedNo: false,
    };
  },
  mounted() {
    let timer = setInterval(() => {
      if (this.goodWordArr.length - 1 > this.goodWordNum) {
        this.goodWordNum++;
      } else {
        clearInterval(timer);
      }
    }, 14000);
  },

  methods: {
    choseABtn(theBtn) {
      if (this.clickedNo === false && this.clickedYes === false) {
        // אם שאלה ראשונה או אחת לפני האחרונה וענו לא
        if ((this.numQues === 0 || this.numQues === 15) && !theBtn) {
          this.isKickedOut = true;
          this.$emit("hide-mador-till-logo");
          return;
        }
        //כדי שיופיע מחלקה של אחרי לחיצה
        if (theBtn) {
          this.clickedYes = true;
        } else {
          this.clickedNo = true;
        }
        //מעביר לשאלה הבאה ומחשב
        let clickTimer = setTimeout(() => {
          if (this.numQues !== 0) {
            let arr;
            if (theBtn) {
              arr = this.questions[this.numQues].indexYesRoles;
            } else {
              arr = this.questions[this.numQues].indexNoRoles;
            }
            this.addCountAccordingToChoise(arr);
          }

          // קידום לשאלה הבאה
          if (this.numQues < this.questions.length - 1) {
            this.numQues++;
          } else if (this.numQues === this.questions.length - 1) {
            this.showResult();
          }

          this.clickedYes = false;
          this.clickedNo = false;
          clearTimeout(clickTimer);
        }, 1000);
      }
    },

    addCountAccordingToChoise(arr) {
      for (let i = 0; i < arr.length; i++) {
        this.arrRoles[arr[i]]++;
      }
    },

    checkWhichRoleBiggestCount() {
      let maxCounter = -1;
      let theRole = [];

      for (let i = 0; i < this.arrRoles.length; i++) {
        const count = this.arrRoles[i];

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
        console.log(resultArr[randomIndex]);
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
}

.quiz-container {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
}

.num-ques-container {
  position: absolute;
  right: 1rem;
  top: 1rem;
  width: 3rem;
  height: 3rem;
  display: flex;
  color: white;
  background-color: #157145;
  align-items: center;
  justify-content: center;
  border-radius: 100%;
  font-weight: bold;
}

.dots {
  width: 4rem;
}

.dots-container {
  width: 50rem;
  display: flex;
  animation: floatUpDown-25f0e682 3s ease-in-out infinite;
}

.up {
  margin-bottom: -10rem;
  flex-direction: row-reverse;
}

.down {
  margin-top: -10rem;
}
.question {
  font-size: 2rem;
  font-weight: bold;
  animation: floatUpDown-25f0e682 3s ease-in-out infinite;
  width: 40rem;
  height: 8rem;
  background-color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 2rem;
  margin: -4rem;
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
  margin-top: -10rem;
}

.btn-container {
  width: 13rem;
  height: 13rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.btn {
  cursor: pointer;
  width: 8rem;
}

.talk-bubble {
  background-image: url("/media/talkBubble.png");
  background-repeat: no-repeat;
  background-size: 100% 100%;
  height: 7rem;
  width: 10rem;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  left: 4rem;
}

.soldier {
  width: 15rem;
}

.soldier-container {
  position: absolute;
  bottom: -10rem;
  left: 5rem;
  display: flex;
  flex-direction: row-reverse;
  pointer-events: none;
  animation: pop 30s ease-in-out infinite; /* משך כולל של 60 שניות */
}

@keyframes pop {
  0%,
  15% {
    bottom: -10rem; /* מצב התחלה - למטה */
  }
  20% {
    bottom: -30rem; /* קפיצה למעלה */
  }
  50% {
    bottom: -30rem; /* נשאר למעלה במשך 40% מהאנימציה */
  }
  55% {
    bottom: -10rem;
  }

  70% {
    bottom: -10rem; /* חזרה למטה */
  }
  75% {
    bottom: -30rem; /* השהיה למטה עד הסיבוב הבא */
  }
  90% {
    bottom: -30rem;
  }
}
.clicked-heart {
  transition: all 0.5s ease;
  width: 10rem;
  filter: drop-shadow(0 0 0.4rem rgb(255, 255, 255));
}

@media screen and (max-width: 670px) {
  .dots-container {
    width: 97%;
  }
}
@media screen and (max-width: 500px) {
  .soldier-container {
    left: -2rem;
  }

  #quiz {
    height: 91vh;
  }

  .question {
    width: 90%;
  }

  .quiz-container {
    height: 90vh;
  }
}
</style>
