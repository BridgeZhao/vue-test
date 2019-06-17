<template>
  <div class="container">
    <div class="wrapper">
      <swiper :options='swiperOptions'>
        <swiper-slide>
          <img class="gallary-img" src="https://img1.qunarzz.com/p/tts8/1811/af/a69e5f481e2cae02.jpg_r_1280x840x90_45623050.jpg">
        </swiper-slide>
        <swiper-slide>
          <img class="gallary-img" src="https://img1.qunarzz.com/p/tts6/1811/4c/d13fea4a41b0c502.jpg_r_1280x840x90_81e9a69e.jpg">
        </swiper-slide>
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'commonGallary',
  data () {
    return {
      swiperOptions: {
        // pagination: '.swiper-pagination',  不兼容
        pagination: {
          el: '.swiper-pagination',
          type: 'fraction'
        },
        // paginationType: 'fraction' 不兼容
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
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
      overflow: hidden
      height: 0
      width:100%
      padding-bottom: 70%
      .gallary-img
        width:100%
    .swiper-pagination
      color:#fff
</style>
