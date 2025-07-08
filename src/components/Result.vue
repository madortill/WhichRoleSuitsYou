<template>
  <div id="result">
    <img
      @click="toRestart"
      src="/media/restartIcon/blue.svg"
      alt="restart"
      class="restart"
    />
<p class="fix-text top-text">איזה כיף {{ userName }}!</p>
<p class="fix-text">קיבלת:</p>
    <p class="headline">{{ arrRoles[resultIndex].name }}</p>
    <img class="role-img" :src="getRoleSrc()" alt="roleImg" />
    <img class="soldier" src="/media/soldier/finish.png" alt="soldier" />
  </div>
</template>

<script>
export default {
  name: "result",

  props: ["resultIndex", "userName"],
  data() {
    return {
      arrRoles: [
        {
          name: "מפקד/ת נוער",
          imgUrl: "media/role/role0.jpeg",
        },
        {
          name: 'מפק"צ חינוך',
          imgUrl: "media/role/role1.jpeg",
        },
        {
          name: 'מש"ק/ית חו"יה',
          imgUrl: "media/role/role2.jpeg",
        },
        {
          name: 'מש"ק/ית הוראה והדרכה',
          imgUrl: "media/role/role3.jpeg",
        },
        {
          name: 'מש"ק/ית גשרים',
          imgUrl: "media/role/role4.jpeg",
        },
        {
          name: 'מש"ק/ית תקומה',
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
  color: #157145;
  font-size: 2rem ;
  font-weight: bold;
}

.headline {
 
  font-size: 2.5rem;
  margin-top: 5rem;
  color: #2180c3;
}

.role-img {
  border-radius: 2rem;
    max-height: 23rem;
    max-width: 95%;
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

.fix-text {
  margin: 0rem;
}

.top-text {
  margin-top: 6rem;
}
@media screen and (max-width: 500px) {
  #result {
    height: 91vh;
  }
}
</style>
