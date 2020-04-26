<template>
  <div class="content-holder">
    <div v-for="(src, index) in iconsSrcArray" :key="index" class="content-window">
      <ContentImage
        v-if="renderIcons"
        :src="src"
        :index="index"
        :iconsSrcArray="iconsSrcArray"
        :svgClasses="svgClasses"
      />

      <div v-if="renderTitles" :class="contentTitleClasses">{{titlesArray[index]}}</div>

      <ContentInfo
        :infosArray="infosArray"
        :index="index"
        :infosClasses="infosClasses"
      />
    </div>
  </div>
</template>

<script>
import ContentImage from "./ContentImage.vue";
import ContentInfo from "./ContentInfo.vue";

export default {
  name: "Content",
  components: {
    ContentImage,
    ContentInfo
  },
  props: {
    renderIcons: {
      type: Boolean,
      required: true
    },
    iconsSrcArray: {
      type: Array,
      required: true
    },
    svgClasses: {
      type: String,
      required: true
    },
    renderTitles: {
      type: Boolean,
      required: true
    },
    titlesArray: {
      type: Array,
      required: true
    },
    contentTitleClasses: {
      type: String,
      required: true
    },
    infosArray: {
      type: Array,
      required: true
    },
    infosClasses: {
      type: String,
      required: true
    },
    screenWidth: {
      type: Number,
      required: true
    }
  }
};
</script>

<style scoped lang="sass">
@import "@/assets/vars.sass"

@media (min-width: $mobile-width-start) and (max-width: $tablet-width-end)
  .content-holder
    width: 100%
    display: flex
    flex-wrap: wrap
    justify-content: space-between
    padding-top: 40px
@media (min-width: $tablet-width-start) and (max-width: $pc-width-1024-end)
  .content-holder
    flex-direction: column
    width: $content-window-tablet-width

@media (min-width: $pc-width-1024-start)
  .content-holder
    display: flex
    flex-wrap: wrap
    justify-content: space-between
@media (min-width: $tablet-width-start) and (max-width: $tablet-width-end)
  .content-window
    width: $content-window-tablet-width
@media (min-width: $pc-width-1024-start) and (max-width: $pc-width-1024-end)
  .content-holder
    width: $content-window-pc-width
  .content-window
    width: $content-window-pc-width
@media (min-width: $pc-width-1280-start) and (max-width: $pc-width-1280-end)
  .content-holder
    width: $content-window-pc-1280-width
  .content-window
    width: $content-window-pc-1280-width
@media (min-width: $pc-width-1440-start)
  .content-holder
    width: $content-window-pc-1440-width
  .content-window
    width: $content-window-pc-1440-width
  
.title
  width: inherit
  height: $mobile-height-1
  padding-top: $content-padding-top-2
  font-size: $font-size-1
  line-height: $line-height-1
  color: $text-color
  font-weight: $font-weight-bold
</style>
