<template>
  <div id="lomda-info">
    <p class="btn-info" @click="showTheInfo">i</p>
    <div class="info-container" v-if="showInfo">
      <p @click="closeInfo" class="close-info">X</p>
      <ul class="info-list">
        <li class="info" v-for="(subTitle, title) in infoObject" :key="title">
          <span class="info-title">{{ title }}</span
          ><br />
          <span>{{ subTitle }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "lomda-info",
  data() {
    return {
      infoObject: {
        "מפתחת לומדה ראשית:": 'רב"ט דני שריקי',
        "גרפיקאית:": 'רב"ט דני שריקי',
        "מומחה תוכן:": 'סמ"ר עומר',
        'רמ"ד טי"ל:': 'רס"מ עדן בן חמו',
        "גרסה:": "יולי 2025",
      },
      showInfo: false,
    };
  },
  methods: {
    closeInfo() {
      this.showInfo = false;
    },
    showTheInfo() {
      this.showInfo = true;
    },
  },
};
</script>

<style scoped>
.btn-info {
  background-color: #2180c3;
  color: white;
  top: 1rem;
  left: 1rem;
  width: 2rem;
  height: 2rem;
  display: flex;
  position: absolute;
  align-items: center;
  justify-content: center;
  border-radius: 100%;
  cursor: pointer;
}

.info-container {
  z-index: 3;
  background-color: white;
  border-radius: 1rem;
  width: 15rem;
  animation: windowShow 0.2s linear forwards;
  font-size: 1.5rem;
  position: absolute;
    top: 1rem;
    left: 5rem;
}

.info-list {
  display: flex;
  width: 100%;
  margin-top: -3rem;
  padding: 0%;
  flex-direction: column;
}

.info-title {
  font-weight: bold;
}

.info {
  margin-bottom: 1.2rem;
  font-weight: normal;
}

.close-info {
  margin-left: 12rem;
  cursor: pointer;
  font-size: 1.8rem;
}

@keyframes windowShow {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
