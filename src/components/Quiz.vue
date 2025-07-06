<template>
  <div id="quiz">
    <p class="question">{{questions[numQues].title}}</p>
    <div class="btns-container">
      <img class="btn" src="/media/noBtn.png" alt="no" @click="choseABtn(false)" />
      <img class="btn" src="/media/yesBtn.png" alt="yes" @click="choseABtn(true)" />
    </div>
  </div>
</template>

<script>
export default {
  name: "quiz",

  components: {},
  props: [],
  data() {
    return {
        questions: [
      {
        Qnum: 0,
        title: "האם את/ה אוהב/ת שטח?",
        indexYesRoles: [0, 1],
        indexNoRoles: [2, 3, 4, 5],
      },
      {
        Qnum: 1,
        title: "האם את/ה אוהב/ת לעבוד עם מחשבים?",
        indexYesRoles: [4],
        indexNoRoles: [0, 1, 2, 3, 5],
      },
      {
        Qnum: 2,
        title: "האם את/ה אוהב/ת את ההיסטוריה של הארץ?",
        indexYesRoles: [2],
        indexNoRoles: [0, 1, 3, 4, 5],
      },
      {
        Qnum: 3,
        title: "האם את/ה אוהב/ת לעבוד עם ילדים?",
        indexYesRoles: [5],
        indexNoRoles: [0, 1, 2, 3, 4],
      },
      {
        Qnum: 4,
        title: "האם את/ה אוהב/ת את השפה העברית?",
        indexYesRoles: [1, 3],
        indexNoRoles: [0, 2, 4, 5],
      },
      {
        Qnum: 5,
        title: 'האם את/ה מתעניינ/ת ביחידות השונות בצה"ל?',
        indexYesRoles: [0],
        indexNoRoles: [1, 2, 3, 4, 5],
      },
      {
        Qnum: 6,
        title: "האם את/ה אוהב/ת לעבוד עם בני נוער?",
        indexYesRoles: [0, 4, 5],
        indexNoRoles: [1, 2, 3],
      },
      {
        Qnum: 7,
        title: "האם את/ה אוהב/ת לעבוד בצוות?",
        indexYesRoles: [1],
        indexNoRoles: [0, 2, 3, 4, 5],
      },
      {
        Qnum: 8,
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
  
    };
  },
  methods: {
    choseABtn(theBtn){
        if(theBtn) {

        } else {

        }
        if(this.numQues< 9) {
            this.numQues++;
        }
    },
},
};
</script>

<style scoped>
#quiz {
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
}

.btns-container {
display: flex;
align-items: center;
    width: 100vw;
    justify-content: space-evenly;
}

.btn {
    cursor: pointer;
    width: 7rem;
}
@media screen and (max-width: 480px) {
}
</style>
