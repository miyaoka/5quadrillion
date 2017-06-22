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
        <img src="../assets/img/currency/yen.png">
      </span>
    </div>
  </div>
</template>

<script>

export default {
  props: {
    exponent: Number,
    base: Number
  },
  methods: {
    numImgPath (num) {
      return require(`@/assets/img/number/${num}.png`)
    },
    baseImgPath (exponent) {
      return require(`@/assets/img/unit/base10000/${Math.floor(exponent)}.png`)
    },
    currencyImgPath (exponent) {
      return require(`@/assets/img/unit/base10000/${Math.floor(exponent)}.png`)
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
