<template>
  <div class="container" @click="handleGallaryClick">
    <div class="wrapper">
      <swiper :options='swiperOptions'>
        <swiper-slide v-for='(item, key) in imgs' :key='key'>
          <img class="gallary-img" :src="item">
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'commonGallary',
  props: {
    imgs: {
      type: Array
    }
  },
  methods: {
    handleGallaryClick () {
      this.$emit('close')
    }
  },
  data () {
    return {
      swiperOptions: {
        // pagination: '.swiper-pagination',  不兼容
        pagination: {
          el: '.swiper-pagination',
          type: 'fraction'
        },
        observeParents: true,
        observer: true
        // paginationType: 'fraction' 不兼容
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .container >>> .swiper-container
    overflow: inherit
  .container
    display: flex
    flex-direction: column
    justify-content: center
    z-index: 99
    position: fixed
    left: 0
    right: 0
    top: 0
    bottom: 0
    background: #000
    .wrapper
      height: 0
      width:100%
      padding-bottom: 70%
      .gallary-img
        width:100%
    .swiper-pagination
      color:#fff
</style>
