<template>
  <div class="header-holder">
    <div :class="textClasses">{{text}}</div>
    <div :class="titleClasses">{{title}}</div>
    <div :class="lastUpdatedClasses">{{lastUpdated}}</div>
    <div :class="subTitleClasses">{{subTitle}}</div>
    
    <Footer
      v-if="screenWidth >= 1024"
      :footerText="footerText"
      :footerClasses="footerClasses"
    />
  </div>
</template>

<script>
import Footer from "./Footer.vue";

export default {
  name: "Header",
  components: {
    Footer
  },
  props: {
    text: {
      type: String,
      required: true
    },
    textClasses: {
      type: String,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    titleClasses: {
      type: String,
      required: true
    },
    lastUpdated: {
      type: String,
      required: true
    },
    lastUpdatedClasses: {
      type: String,
      required: true
    },
    subTitle: {
      type: String,
      required: true
    },
    subTitleClasses: {
      type: String,
      required: true
    },
    screenWidth: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      footerText: "Learn More",
      footerClasses: "footer-holder",
    };
  }
};
</script>

<style scoped lang="sass">
@import "@/assets/vars.sass"

@media (min-width: $pc-width-1024-start)
  .header-holder
    position: relative
@media (min-width: $pc-width-1024-start) and (max-width: $pc-width-1024-end)
  .header-holder
    width: $content-window-pc-width
@media (min-width: $pc-width-1280-start) and (max-width: $pc-width-1280-end)
  .header-holder
    width: $content-window-pc-1280-width
@media (min-width: $pc-width-1440-start)
  .header-holder
    width: $content-window-pc-1440-width

.top-text
  width: inherit
  height: $mobile-height-1
  font-size: $font-size-1
  font-style: $font-style-normal
  font-weight: $font-weight-normal
  line-height: $line-height-1
  color: rgba(36, 49, 67, 0.6)
  mix-blend-mode: $mix-blend-mode-normal

.title
  font-size: $font-size-3
  line-height: $line-height-2
  color: $text-color
  padding-top: $padding-top-1
@media (min-width: $mobile-width-start) and (max-width: $mobile-width-end)
  .title
    height: $mobile-height-2
@media (min-width: $tablet-width-start) and (max-width: $tablet-width-end)
  .title
    width: $tablet-width
    height: $tablet-height-1

.bottom-text
  font-size: $font-size-1
  line-height: $line-height-1
  color: $text-color-3
  mix-blend-mode: $mix-blend-mode-normal
  padding-top: $padding-top-1
@media (min-width: $mobile-width-start) and (max-width: $mobile-width-end)
  .bottom-text
    height: $mobile-height-1
@media (min-width: $tablet-width-start) and (max-width: $tablet-width-end)
  .bottom-text
    width: $tablet-width
    height: $mobile-height-1

.sub-title
  font-size: $font-size-2
  font-style: $font-style-normal
  font-weight: $font-weight-normal
  line-height: $line-height-1
  color: $text-color
  padding-top: $padding-top-2
@media (min-width: $mobile-width-start) and (max-width: $mobile-width-end)
  .sub-title
    height: $mobile-height-3
@media (min-width: $tablet-width-start) and (max-width: $tablet-width-end)
  .sub-title
    width: calc( 100% - #{$pc-margin-right-2} )
    height: $tablet-height-2
</style>
