<template>
  <img :src="getImage" :class="featureIconClasses">
</template>

<script>
export default {
  name: "GetSvg",
  props: {
    src: {
      type: String,
    },
    featureIconClasses: {
      type: String,
    }
  },
  computed: {
    getImage() {
      return require(`@/assets/${this.src}`);
    }
  }
};
</script>

<style scoped lang="sass">
.feature-icon
  border: 3px dashed #b5b5b5
  border-radius: 3px
</style>
