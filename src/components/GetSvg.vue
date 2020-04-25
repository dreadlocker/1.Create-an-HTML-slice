<template>
  <img :src="getImage" :class="svgClasses">
</template>

<script>
export default {
  name: "GetSvg",
  props: {
    src: {
      type: String,
      required: true
    },
    svgClasses: {
      type: String,
      required: true
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
.svg
  border: 3px dashed #b5b5b5
  border-radius: 3px
</style>
