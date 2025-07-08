<template>
  <div id="kicked-out">
    <img
      @click="toRestart"
      src="/media/restartIcon/white.svg"
      alt="restart"
      class="restart"
    />
    <p class="text">{{genderArr[0]}}</p>
    <p class="headline">{{genderArr[1]}}</p>
    <img class="soldier" src="/media/soldier/kickedOut.png" alt="soldier" />
    <img class="mador-till" src="/media/MadorTill/white.svg" alt="mador-till" />
  </div>
</template>

<script>
export default {
  name: "kicked-out",

  props: ['userGender'],
  data() {
    return {
      changeBg: false,
      maleArr: ['באסה לך מלש"ב יקר', 'אז כדאי שתחפש בחיל אחר...'],
      femaleArr: ['באסה לך מלש"בית יקרה', 'אז כדאי שתחפשי בחיל אחר...'],
    };
  },
  mounted() {
    // בזמן שהקומפוננטה נטענת

    let timer = setTimeout(() => {
      this.changeBg = true;
      clearTimeout(timer);
    }, 2000);
  },
  methods: {
    toRestart() {
      window.location.reload();
    },
  },
  computed: {
  genderArr() {
    return this.userGender === 'male' ? this.maleArr : this.femaleArr;
  }
}
};
</script>

<style scoped>
#kicked-out {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  font-weight: bold;
  animation: fadeIn 2s ease-in-out forwards; /* משך כולל של 60 שניות */
}

@keyframes fadeIn {
  from {
    background-color: #cfedf8;
    opacity: 0;
  }
  to {
    background-color: #5e6061;
    color: white;
    opacity: 1;
  }
}

.text {
  margin-top: 10rem;
  font-size: 1.5rem;
}

.headline {
  font-size: 2.5rem;
  margin-top: 3rem;
}

.soldier {
  width: 29rem;
  position: absolute;
  bottom: -16rem;
  right: 5rem;
}

.restart {
  position: absolute;
  right: 1rem;
  top: 1rem;
  width: 5rem;
  cursor: pointer;
}
@media screen and (max-width: 500px) {
  #kicked-out {
    height: 91vh;
  }
}
</style>
