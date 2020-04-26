<template>
  <div :class="featureTitleClasses">{{title}}</div>
</template>

<script>
export default {
  name: "ContentTitle",
  props: {
    title: {
      type: String,
      validator: (str) => str.length <= 40
    },
    featureTitleClasses: {
      type: String,
    }
  }
};
</script>

<style scoped lang="sass">
@import "@/assets/vars.sass"

.feature-title
  width: inherit
  height: $mobile-height-1
  padding-top: $content-padding-top-2
  font-size: $font-size-1
  line-height: $line-height-1
  color: $text-color
  font-weight: $font-weight-bold
</style>
