<template>
  <div :class="infosClasses">
    <span v-if="typeof infosArray[index] === 'string'">{{infosArray[index]}}</span>
    <span
      v-else
      v-for="(obj, index) in infosArray[index]"
      :key="index"
      :class="{[obj.className]: obj.className}"
    >{{obj[`text${index+1}`]}}</span>
  </div>
</template>

<script>
export default {
  name: "ContentInfo",
  props: {
    infosArray: {
      type: Array,
      required: true
    },
    index: {
      type: Number,
      required: true
    },
    infosClasses: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped lang="sass">
@import "@/assets/vars.sass"

.info
  width: inherit
  padding: $content-padding-top-1 0 $content-padding-bottom-1
  font-style: $font-style-normal
  font-weight: $font-weight-normal
  font-size: $font-size-1
  line-height: $line-height-1
  color: rgba(36, 49, 67, 0.9)
.colored
  color: $text-color-2
</style>
