<template>
  <div>
    <div class="banner">
      <img src="https://img1.qunarzz.com/p/tts9/1811/d8/34305b5503023902.jpg_r_640x420x90_f0a47f76.jpg" class="banner-img" @click="handleBannerClick">
      <div class="banner-info">
        <div class="banner-title">
          成都出发-跟团游
        </div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe615;</span>
          39
        </div>
      </div>
    </div>
    <common-gallary
     :imgs='imgs'
      v-show='showGallary'
      @close='handleGallaryClose'></common-gallary>
  </div>
</template>

<script>
import commonGallary from 'common/gallary/gallary'
export default {
  name: 'detailBanner',
  data () {
    return {
      showGallary: false,
      imgs: ['https://img1.qunarzz.com/p/tts8/1811/af/a69e5f481e2cae02.jpg_r_1280x840x90_45623050.jpg', 'https://img1.qunarzz.com/p/tts6/1811/4c/d13fea4a41b0c502.jpg_r_1280x840x90_81e9a69e.jpg']
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleGallaryClose () {
      this.showGallary = false
    }
  },
  components: {
    commonGallary
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus" scoped>
  .banner
    position:relative
    overflow:hidden
    height:0
    padding-bottom:55%
    .banner-img
      width:100%
    .banner-info
      display: flex
      position: absolute
      left:0
      right:0
      bottom:0
      line-height:.6rem
      color:#fff
      background-image: linear-gradient(top, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8))
      .banner-title
        flex:1
        font-size:.32rem
        padding: 0 .2rem
      .banner-number
        height: .4rem
        line-height: .4rem
        margin-top: .14rem
        padding:0 .4rem
        border-radius: .2rem
        background:rgba(0, 0, 0, .8)
        font-size: .24rem
        .banner-icon
          font-size:0.24rem
</style>
