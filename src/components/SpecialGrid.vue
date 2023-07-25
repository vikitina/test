<template lang="pug">
.special-grid(@click="onClick", ref="gridElement")
  MoovieBall(:x="xCoord", :y="yCoord")
</template>
<script>
import MoovieBall from "./MoovieBall.vue";
export default {
  data() {
    return {
      xCoord: 0,
      yCoord: 0,
      width: 0,
      height: 0,
    };
  },
  components: {
    MoovieBall,
  },
  methods: {
    onClick(e) {
      this.xCoord = this.getPreparedX(e);
      this.yCoord = this.getPreparedY(e);
      this.$emit("updateStatistic", {
        x: this.getStatisticX,
        y: this.getStatisticY,
      });
    },
    getPreparedX(e) {
      return e.offsetX >= 0 && e.offsetX <= this.width
        ? e.offsetX
        : this.xCoord;
    },
    getPreparedY(e) {
      return e.offsetY >= 0 && e.offsetY <= this.height
        ? e.offsetY
        : this.yCoord;
    },
  },

  computed: {
    getStatisticX() {
      return this.xCoord - this.width * 0.5 >= 0
        ? this.xCoord - this.width * 0.5
        : -1 * (this.width * 0.5 - this.xCoord);
    },
    getStatisticY() {
      return this.yCoord - this.height * 0.5 <= 0
        ? this.height * 0.5 - this.yCoord
        : -1 * (this.yCoord - this.height * 0.5);
    },
  },
  mounted() {
      const element = this.$refs.gridElement;
      this.width = element.offsetWidth;
      this.height = element.offsetHeight;
      this.xCoord = this.width * 0.5;
      this.yCoord = this.height * 0.5;
      this.$emit("updateStatistic", {
        x: this.getStatisticX,
        y: this.getStatisticY,
      });
  },
};
</script>
<style lang="scss" scoped>
.special-grid {
  width: 280px;
  height: 280px;
  border: 2px solid blue;
  border-radius: 5px;
  position: relative;

  background-image: repeating-linear-gradient(#ccc 0 1px, transparent 1px 100%),
    repeating-linear-gradient(90deg, #ccc 0 1px, transparent 1px 100%);
  background-size: 70px 70px;
  &::before {
    content: "";
    width: 6px;
    height: 6px;
    background: red;
    border-radius: 50%;
    display: block;
    position: absolute;
    top: calc(50% - 3px);
    left: calc(50% - 3px);
  }
  &:hover {
    box-shadow: 0 0 20px 2px blue;
  }
}
</style>