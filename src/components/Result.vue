<template>
  <div id="result">
    <p class="headline">{{ arrRoles[resultIndex].name }}</p>
    <img class="role-img" :src="arrRoles[resultIndex].imgUrl" alt="roleImg" />
  </div>
</template>

<script>
export default {
  name: "result",

  props: ["resultIndex"],
  data() {
    return {
      arrRoles: [
        {
          name: "מפקד/ת נוער",
          imgUrl: "/media/role/role0.jpeg",
        },
        {
          name: 'מפק"צ חינוך',
          imgUrl: "/media/role/role1.jpeg",
        },
        {
          name: 'מש"ק/ית חו"יה',
          imgUrl: "/media/role/role2.jpeg",
        },
        {
          name: 'מש"ק/ית הוראה והדרכה',
          imgUrl: "/media/role/role3.jpeg",
        },
        {
          name: 'מש"ק/ית גשרים',
          imgUrl: "/media/role/role4.jpeg",
        },
        {
          name: 'מש"ק/ית תקומה',
          imgUrl: "/media/role/role5.jpeg",
        },
      ],
    };
  },
  methods: {},
};
</script>

<style scoped>
#result {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
}

.headline {
  font-weight: bold;
  font-size: 2.5rem;
}
.role-img {
  width: 20rem;
}
@media screen and (max-width: 600px) {
}
</style>
