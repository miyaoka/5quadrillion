<template>
  <img
    :src="imgPath"
    @click="onClick()"
  >
</template>

<script>
export default {
  props: {
    value: String,
    list: Array,
    context: Function
  },
  computed: {
    imgPath () {
      return this.context(`./${this.list[this.selectedIndex]}.png`)
    },
    selectedIndex () {
      const i = this.list.findIndex(v => v === this.value)
      return i === -1 ? 0 : i
    }
  },
  methods: {
    onClick () {
      this.$emit('input', this.list[(this.selectedIndex + 1) % this.list.length])
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
