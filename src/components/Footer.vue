<template>
  <div :class="footerClasses">
    <span class="footer-text">{{footerText}}</span>
    <svg width="12" height="12" viewBox="0 0 12 12" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path d="M8.58579 5L5.29289 1.70711C4.90237 1.31658 4.90237 0.683418 5.29289 0.292893C5.68342 -0.0976311 6.31658 -0.0976311 6.70711 0.292893L11.7071 5.29289C12.0976 5.68342 12.0976 6.31658 11.7071 6.70711L6.70711 11.7071C6.31658 12.0976 5.68342 12.0976 5.29289 11.7071C4.90237 11.3166 4.90237 10.6834 5.29289 10.2929L8.58579 7H1C0.447715 7 0 6.55228 0 6C0 5.44772 0.447715 5 1 5H8.58579Z" fill="#408BEA"/>
    </svg>
  </div>
</template>

<script>
export default {
  name: "Footer",
  props: {
    footerText: {
      type: String,
      required: true
    },
    footerClasses: {
      type: String,
      required: true
    }
  }
};
</script>

<style scoped lang="sass">
@import "@/assets/vars.sass"

.footer-holder
  width: $footer-holder-width
  height: 32px
  font-size: $line-height-1
  line-height: 32px
  color: $text-color-2
@media (min-width: $mobile-width-start) and (max-width: $tablet-width-end)
  .footer-holder
    padding-bottom: 80px
@media (min-width: $pc-width-1024-start)
  .footer-holder
    position: absolute
@media (min-width: $pc-width-1024-start) and (max-width: $pc-width-1024-end)
  .footer-holder
    bottom: 104px
@media (min-width: $pc-width-1280-start)
  .footer-holder
    bottom: 120px

.footer-text
  width: $footer-text-width
  margin-right: $space-between-footer-text-icon
</style>
