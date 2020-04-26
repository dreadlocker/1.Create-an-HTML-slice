<template>
  <div class="header-holder">
    <div v-if="groupDescriptorClasses" :class="groupDescriptorClasses">{{groupDescriptor}}</div>
    <div :class="sliceTitleClasses">{{sliceTitle}}</div>
    <div :class="sliceDescriptorClasses">{{sliceDescriptor}}</div>
    <div :class="sliceLeadClasses">{{sliceLead}}</div>
    
    <Footer
      v-if="screenWidth >= 1024"
      :sliceLink="sliceLink"
      :sliceLinkClasses="sliceLinkClasses"
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
    groupDescriptor: {
      type: String,
      validator: (str) => str.length <= 30
    },
    groupDescriptorClasses: {
      type: String,
    },
    sliceTitle: {
      type: String,
      required: true,
      validator: (str) => str.length >= 30 && str.length <= 80
    },
    sliceTitleClasses: {
      type: String,
      required: true
    },
    sliceDescriptor: {
      type: String,
      validator: (str) => str.length <= 30
    },
    sliceDescriptorClasses: {
      type: String,
    },
    sliceLead: {
      type: String,
      validator: (str) => str.length >= 60 && str.length <= 200
    },
    sliceLeadClasses: {
      type: String,
    },
    screenWidth: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      sliceLink: "Learn More",
      sliceLinkClasses: "slice-link",
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

.group-descriptor
  width: inherit
  height: $mobile-height-1
  font-size: $font-size-1
  font-style: $font-style-normal
  font-weight: $font-weight-normal
  line-height: $line-height-1
  color: rgba(36, 49, 67, 0.6)
  mix-blend-mode: $mix-blend-mode-normal

.slice-title
  font-size: $font-size-3
  line-height: $line-height-2
  color: $text-color
  padding-top: $padding-top-1
@media (min-width: $mobile-width-start) and (max-width: $mobile-width-end)
  .slice-title
    height: $mobile-height-2
@media (min-width: $tablet-width-start) and (max-width: $tablet-width-end)
  .slice-title
    width: $tablet-width
    height: $tablet-height-1

.slice-descriptor
  font-size: $font-size-1
  line-height: $line-height-1
  color: $text-color-3
  mix-blend-mode: $mix-blend-mode-normal
  padding-top: $padding-top-1
@media (min-width: $mobile-width-start) and (max-width: $mobile-width-end)
  .slice-descriptor
    height: $mobile-height-1
@media (min-width: $tablet-width-start) and (max-width: $tablet-width-end)
  .slice-descriptor
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
