<template>
  <!-- Picture data prop to be used in Images view -->
  <div id="picture-data">
    <a :href="link" target="_blank" class="d-block mb-4 h-100">
      <img
        :class="[
          catImage.isClicked ? catImage.applyBorder : '',
          catImage.imgFluid,
        ]"
        :src="src"
        :alt="alt"
        @click="imgClicked"
      />
    </a>
  </div>
</template>

<script>
// Imports border mixin
import { addBorder } from '@/mixins/addBorder.js'

// Use of mixin to add border and props for image attributes
export default {
  mixins: [addBorder],
  props: {
    link: String,
    src: String,
    alt: String,
  },
}
</script>

<!-- Styling for border box that is added around image when it is clicked
and catImage.isClicked is set to true-->
<style scoped>
.border-on-click {
  border: 5px solid darkgray;
}
</style>
