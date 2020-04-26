<template>
  <div class="content-holder">
    <div v-for="(src, index) in featureIconsSrcArray" :key="index" class="content-window">
      <ContentImage
        v-if="featureIconsSrcArray.length < 9"
        :src="src"
        :featureIconClasses="featureIconClasses"
      />

      <ContentTitle
        :title="featureTitlesArray[index]"
        :featureTitleClasses="featureTitleClasses"
      />

      <ContentInfo
        :textOrArray="featureBodyTextArray[index]"
        :featureBodyTextClasses="featureBodyTextClasses"
        :addExtraClass="index < featureBodyTextArray.length - 1"
      />
    </div>
  </div>
</template>

<script>
import ContentImage from "./ContentImage.vue";
import ContentInfo from "./ContentInfo.vue";
import ContentTitle from "./ContentTitle.vue";

export default {
  name: "Content",
  components: {
    ContentImage,
    ContentInfo,
    ContentTitle
  },
  props: {
    featureIconsSrcArray: {
      type: Array,
      validator: (arr) => arr.length >= 2
    },
    featureIconClasses: {
      type: String,
    },
    featureTitlesArray: {
      type: Array,
      validator: (arr) => arr.length >= 2
    },
    featureTitleClasses: {
      type: String,
    },
    featureBodyTextArray: {
      type: Array,
      required: true,
      validator: (arr) => arr.length >= 2
    },
    featureBodyTextClasses: {
      type: String,
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
</style>
