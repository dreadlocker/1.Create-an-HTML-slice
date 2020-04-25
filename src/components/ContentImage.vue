<template>
  <div :class="[{'relative': isExclusive}]">
    <GetSvg :src="getImageSrc" :svgClasses="svgClasses" />
    <div v-if="isExclusive" :class="isExclusive">{{isExclusive}}</div>
  </div>
</template>

<script>
import GetSvg from "./GetSvg.vue";

export default {
  name: "",
  components: {
    GetSvg
  },
  props: {
    src: {
      type: [String, Array],
      required: true
    },
    index: {
      type: Number,
      required: true
    },
    iconsSrcArray: {
      type: Array,
      required: true
    },
    svgClasses: {
      type: String,
      required: true
    }
  },
  computed: {
    getImageSrc() {
      return typeof this.iconsSrcArray[this.index] === "string" ? this.iconsSrcArray[this.index] : this.iconsSrcArray[this.index][0];
    },
    isExclusive() {
      return (Array.isArray(this.iconsSrcArray[this.index]))
        ? this.iconsSrcArray[this.index][1]
        : null;
    }
  }
};
</script>

<style scoped lang="sass">
@import "@/assets/vars.sass"

.relative
  position: relative
.exclusive
  position: absolute
  bottom: -10px
  left: 0
  text-transform: uppercase
  height: 16px
  font-style: $font-style-normal
  font-weight: $font-weight-bold
  font-size: 11px
  line-height: 16px
  text-align: center
  letter-spacing: 1px
  color: #FFFFFF
  background: $text-color-3
  border-radius: 4px
  padding: 0 4px
</style>
