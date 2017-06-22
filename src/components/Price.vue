<template>
  <div class="container">
    <div class="price">
      <img
        v-for="num in nums"
        :src="numImgPath(num)"
      >
    </div>
    <div class="unit">
      <img
        v-if="this.exponent >= 1"
        :src="baseImgPath(exponent)"
      >
      <slot></slot>
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
      return String(
        Math.floor(
          Math.ceil(
            Math.pow(this.base, this.exponent % 1) * this.base
          ) / this.base
        )
      ).split('')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="postcss" scoped>
.container {
  white-space: nowrap;
  display:inline-block;
}
.price {
  display: inline-flex;
  margin: 0 0 0 10px;

  & img {
    margin: 0 -10px;
  }
}
.unit {
  display: inline-flex;
  margin: 0 16px 0 0;

  & img {
    margin: 0 -16px;
  }
}
</style>
