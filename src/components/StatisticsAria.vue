<template lang="pug">
.text {{ statistics }}
</template>
<script>
export default {
    props: {
        statistics: String
    }
}
</script>
<style lang="scss">
.text{
    position: absolute;
    right: 0;
    top: calc(100% + 30px);

}
</style>
