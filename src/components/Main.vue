<template>
  <div>
    <price
      :exponent="exponent"
      :base="base"
      v-model="currency"
    >
      <cycle-img
        v-model="currency"
        :list="[
          'yen',
          'dollar'
        ]"
        :context="require.context('@/assets/img/currency/', false, /\.png$/)"
      ></cycle-img>
    </price>
    <cycle-img
      v-model="verb"
      :list="[
        'want',
        'dontwant'
      ]"
      :context="require.context('@/assets/img/verb/', false, /\.png$/)"
    ></cycle-img>
    <money-slider
      v-model="exponent"
      :max="expoMax"
      :isMobile="true"
    ></money-slider>
  </div>
</template>

<script>
import Price from '@/components/Price'
import CycleImg from '@/components/CycleImg'
import MoneySlider from '@/components/MoneySlider'

const base = 10000
const max = 5000000000000000

export default {
  name: 'main',
  components: {
    Price,
    CycleImg,
    MoneySlider
  },
  data () {
    return {
      currency: 'yen',
      verb: 'want',
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
