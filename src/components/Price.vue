<template>
  <div>
    <div>
      <img
        v-for="num in nums"
        :src="numImgPath(num)"
        class="price"
      >
      <span class="unit">
        <img
          v-if="this.exponent >= 1"
          :src="baseImgPath(exponent)"
        >
        <slot></slot>
      </span>
    </div>
  </div>
</template>

<script>
const numContexts = require.context('@/assets/img/number/', false, /\.png$/)
const baseContexts = require.context('@/assets/img/unit/base10000/', false, /\.png$/)

export default {
  props: {
    exponent: Number,
    base: Number
  },
  methods: {
    numImgPath (num) {
      return numContexts(`./${num}.png`)
    },
    baseImgPath (exponent) {
      return baseContexts(`./${Math.floor(exponent)}.png`)
    }
  },
  computed: {
    nums () {
      return String(Math.ceil(Math.pow(this.base, this.exponent % 1))).split('')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.price {
  margin: 0 -10px;
}
.unit img{
  margin: 0 -20px;
}
</style>
