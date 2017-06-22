<template>
  <div class="container">
    <div class="wrapper">
      <div id="desire">
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
        <div class="verb">
          <cycle-img
            v-model="verb"
            :list="[
              'want',
              'dontwant'
            ]"
            :context="require.context('@/assets/img/verb/', false, /\.png$/)"
          ></cycle-img>
        </div>
      </div>

      <money-slider
        v-model="exponent"
        :max="expoMax"
        :isMobile="true"
        class="slider"
      ></money-slider>

      <md-button
        class="md-raised "
        @click="onClickDomToImage"
      >
        <icon name="download"></icon>
        画像を保存
      </md-button>
      <md-button
        class="md-raised"
        @click="onClickTweet"
        disabled
      >
        <icon name="twitter"></icon>
        現在の金額をツイート
      </md-button>

    </div>
  </div>
</template>

<script>
import domtoimage from 'dom-to-image'
import FileSaver from 'file-saver'
import Icon from 'vue-awesome/components/Icon'
import 'vue-awesome/icons/download'
import 'vue-awesome/icons/twitter'

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
    MoneySlider,
    Icon
  },
  data () {
    return {
      currency: 'yen',
      verb: 'want',
      base: base,
      exponent: 1,
      expoMax: Math.log(max) / Math.log(base)
    }
  },
  methods: {
    onClickDomToImage () {
      domtoimage
      .toBlob(document.getElementById('desire'))
      .then(blob => {
        FileSaver.saveAs(blob, 'my-node.png')
      })
    },
    onClickTweet () {
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  height: 100%;
  display: flex;
  align-items: center;
}
.wrapper {
  width: 100%;
}
#desire {
  display: inline-block;
  text-align: center;
}
.slider {
  margin-top:80px;
}
</style>
