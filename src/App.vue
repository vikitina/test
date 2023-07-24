<template lang="pug">
#app.centered
  .blue-block
    SpecialGrid(@updateStatistic="updateStatistic")
    StatisticsAria(:statistics="`0X: ${xCoord}; 0Y: ${yCoord}`")
</template>

<script>
import SpecialGrid from "./components/SpecialGrid.vue";
import StatisticsAria from "./components/StatisticsAria.vue";

export default {
  name: "App",
  data() {
    return {
      xCoord: 0,
      yCoord: 0,
    };
  },
  components: {
    SpecialGrid,
    StatisticsAria,
  },
  methods: {
    updateStatistic(coordinates) {
      this.xCoord = coordinates.x;
      this.yCoord = coordinates.y;
    },
  },
};
</script>

<style lang="scss">
body {
  margin: 0;
  font-family: "Arial", sans-serif;
}

.blue-block {
  position: relative;
}

.centered {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
</style>
