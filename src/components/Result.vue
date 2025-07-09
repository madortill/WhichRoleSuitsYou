<template>
  <div id="result">
    <img
      @click="toRestart"
      src="/media/restartIcon/blue.svg"
      alt="restart"
      class="restart"
    />
    <p class="top-text">איזה כיף {{ userName }}!</p>
    <div class="headline-container">
      <p class="mini-text">קיבלת &nbsp;</p>
      <p class="headline">{{ roleName }}</p>
    </div>

    <p class="text-guide">לעוד פרטים על התפקיד- הדוכן פה ממול</p>

    <div class="img-container">
      <img v-if="resultIndex !== 0" src="/media/grayLace.png" alt="lace" class="gray-lace" />
      <img v-if="resultIndex === 0" src="/media/brownLace.png" alt="lace" class="gray-lace" />

      <img class="role-img" :src="getRoleSrc()" alt="roleImg" />
      <div class="fix-lace"></div>
    </div>

    <img class="soldier" src="/media/soldier/finish.png" alt="soldier" />
  </div>
</template>

<script>
export default {
  name: "result",

  props: ["resultIndex", "userName", "userGender"],
  data() {
    return {
      arrRoles: [
        {
          maleName: "מפקד נוער",
          femaleName: "מפקדת נוער",
          imgUrl: "media/role/role0.jpeg",
        },
        {
          maleName: 'מפק"צ חינוך',
          femaleName:  'מפק"צית חינוך',
          imgUrl: "media/role/role1.jpeg",
        },
        {
          maleName: 'מש"ק חו"יה',
          femaleName:  'מש"קית חו"יה',
          imgUrl: "media/role/role2.jpeg",
        },
        {
          maleName: 'מש"ק הוראה והדרכה',
          femaleName:  'מש"קית הוראה והדרכה',
          imgUrl: "media/role/role3.jpeg",
        },
        {
          maleName: 'מש"ק גשרים',
          femaleName:  'מש"קית גשרים',
          imgUrl: "media/role/role4.jpeg",
        },
        {
          maleName: 'מש"ק תקומה',
          femaleName:  'מש"קית תקומה',
          imgUrl: "media/role/role5.jpeg",
        },
      ],
    };
  },
  computed: {
    baseURL() {
      // Use Vite's built-in import.meta.env to get the base URL
      return import.meta.env.BASE_URL || "/";
    },
    roleName() {
    const role = this.arrRoles[this.resultIndex];
    return this.userGender === "male" ? role.maleName : role.femaleName;
  },
  },
  methods: {
    getRoleSrc() {
      // Dynamically adjust the src path based on the base URL
      return `${this.baseURL}${this.arrRoles[this.resultIndex].imgUrl}`;
    },
    toRestart() {
      window.location.reload();
    },
  },
};
</script>

<style scoped>
#result {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  color: #2180c3;
  font-size: 2rem;
  font-weight: bold;
}

.headline {
  font-size: 3rem;
}

.headline-container {
  font-size: 2.5rem;
  margin-top: 0rem;
  display: flex;
  align-items: baseline; 
  width: 100vw;
  justify-content: center;
}

.mini-text {
  font-size: 1.5rem;
}

.img-container {
  max-width: 95%;
  position: relative;
}

.role-img {
  border-radius: 2rem;
  max-height: 23rem;
  max-width: 95%;
}

.gray-lace {
  position: absolute;
  height: 100%;
  width: 7rem;
}

.fix-lace {
  height: 3rem;
}

.text-guide {
  margin-top: -2rem;
  font-size: 1.5rem;
}

.soldier {
  width: 20rem;
  position: absolute;
  bottom: -12rem;
  left: 0rem;
}

.restart {
  position: absolute;
  right: 1rem;
  top: 1rem;
  width: 5rem;
  cursor: pointer;
}

.top-text {
  margin: 0rem;
  margin-top: 6rem;
  color: #157145;
}
@media screen and (max-width: 500px) {
  #result {
    height: 91vh;
  }
}
</style>
