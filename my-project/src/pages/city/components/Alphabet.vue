<template>
 <ul class="list">
   <li
   class="item"
   v-for="(item, key) in cities"
   :key="key"
   :ref="item.initial"
   @touchstart="handleTouchStart"
   @touchmove="handleTouchMove"
   @touchend="handleTouchEnd"
   @click="handleLetterClick"
   >
 {{item.initial}}</li>
 </ul>
</template>

<script>
export default {
  name: 'cityAlphabet',
  props: {
    cities: Array
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  computed: {
    letters () {
      const letters = []
      for (let i in this.cities) {
        letters.push(this.cities[i].initial)
      }
      return letters
    }
  },
  methods: {
    handleLetterClick (e) {
      this.$emit('change', e.target.innerText)
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => { //  函数截流
          const touchY = e.touches[0].clientY - 79
          const index = Math.floor((touchY - this.startY) / 20)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchEnd () {
      this.touchStatus = false
    }
  }
}
</script>

<style lang="stylus" scoped>
.list
  display:flex
  flex-direction:column
  justify-content:center
  position:absolute
  top:1.58rem
  right:0
  bottom:0
  width:0.4rem
  .item
    line-height:.4rem
    text-aligin:center
    color:#00bcd4
</style>
