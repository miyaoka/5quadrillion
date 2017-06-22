<template>
  <div>
    <money-number
      :num="num"
    ></money-number>
    <money-slider
      v-model="num"
      :max="5000000000000000"
      :isMobile="true"
    ></money-slider>
  </div>
</template>

<script>
import MoneyNumber from '@/components/MoneyNumber'
import MoneySlider from '@/components/MoneySlider'

export default {
  name: 'main',
  components: {
    MoneyNumber,
    MoneySlider
  },
  data () {
    return {
      num: 10000
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
