<template lang="pug">
  .special-ball(:style="`left:${x}px;top:${y}px`")
</template>
<script>
export default {
  props: {
    x: [String, Number],
    y: [String, Number],
  },
};
</script>
<style lang="scss" scoped>
.special-ball {
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: blue;
  box-shadow: 0 0 20px 2px blue;
  position: absolute;
  transition: all 1s;
  transform: translate(-50%, -50%);
}
</style>