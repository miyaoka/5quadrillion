<template>
  <div>
    <vue-slider
      ref="slider"
      :value="value"
      @input="$emit('input', $event)"
      :max="max"
      :isMobile="isMobile"
      :reverse="true"
      :height="24"
      :dotSize="50"
      :speed=".5"
      :interval=".0001"
      :processStyle = "{
        backgroundImage: '-webkit-linear-gradient(left, #ff0000, #3498db)'
      }"
    ></vue-slider>
    {{isMobile}}
  </div>
</template>

<script>
import vueSlider from 'vue-slider-component'

export default {
  components: {
    vueSlider
  },
  props: {
    value: Number,
    max: Number
  },
  data () {
    return {
      val: this.value,
      isMobile: window.ontouchstart
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
