<template>
  <div>
    <price
      :exponent="exponent"
      :base="base"
    ></price>
    <money-slider
      v-model="exponent"
      :max="expoMax"
      :isMobile="true"
    ></money-slider>
  </div>
</template>

<script>
import Price from '@/components/Price'
import MoneySlider from '@/components/MoneySlider'

const base = 10000
const max = 5000000000000000

export default {
  name: 'main',
  components: {
    Price,
    MoneySlider
  },
  data () {
    return {
      base: base,
      exponent: 1,
      expoMax: Math.log(max) / Math.log(base)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
