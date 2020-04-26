<template>
  <div :class="[{'feature-body-text-padding': addExtraClass}, featureBodyTextClasses]">
    <span v-if="typeof textOrArray === 'string'">{{textOrArray}}</span>
    <span
      v-else
      v-for="(obj, index) in textOrArray"
      :key="index"
      :class="{[obj.className]: obj.className}"
    >{{obj["text"]}}</span>
  </div>
</template>

<script>
export default {
  name: "ContentInfo",
  props: {
    textOrArray: {
      type: [String, Array],
      required: true,
      validator: (el) => {
        if(typeof el === "string" && el.length >= 60 && el.length <= 200) {
          return true;
        }
        if(Array.isArray(el)) {
          const textLength = el.map(obj => obj["text"].length).reduce((a, b) => a + b, 0);
          return textLength >= 60 && textLength <= 200;
        }
        return false;
      }
    },
    featureBodyTextClasses: {
      type: String,
      required: true
    },
    addExtraClass: {
      type: Boolean,
      required: true
    }
  }
};
</script>

<style scoped lang="sass">
@import "@/assets/vars.sass"

.feature-body-text
  width: inherit
  font-style: $font-style-normal
  font-weight: $font-weight-normal
  font-size: $font-size-1
  line-height: $line-height-1
  color: rgba(36, 49, 67, 0.9)
.feature-body-text-padding
  padding: $content-padding-top-1 0 $content-padding-bottom-1
.colored
  color: $text-color-2
</style>
