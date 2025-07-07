<template>
    <div id="kicked-out">
<p class="headline">אז חפשו בחיל אחר...</p>
<img class="soldier" src="/media/soldier/kickedOut.png" alt="soldier"/>

    </div>
  </template>
  
  <script>
  export default {
    name: "kicked-out",
  
    props: [],
    data() {
      return {
      };
    },
    methods: {
   
    },
  };
  </script>
  
  <style scoped>
#kicked-out{
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
}

.headline {
    font-weight: bold;
    font-size: 2rem;
}

.soldier {
  width: 29rem;
    position: absolute;
    bottom: -16rem;
    right: 5rem;
}
  @media screen and (max-width: 600px) {

  }
  </style>
  