<template>
  <div id="kicked-out">
    <p class="text">באסה לך מלש"ב/ית יקר/ה</p>
    <p class="headline">אז כדאי שתחפש/י בחיל אחר...</p>
    <img class="soldier" src="/media/soldier/kickedOut.png" alt="soldier" />
  </div>
</template>

<script>
export default {
  name: "kicked-out",

  props: [],
  data() {
    return {};
  },
  methods: {},
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
@media screen and (max-width: 500px) {
}
</style>
