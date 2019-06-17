<template>
    <div class="list" ref="wrapper">
      <!-- ref操作dom -->
        <div>
            <div class="area">
              <div class="title border-topbottom">当前城市</div>
              <div class="button-list">
                 <div class="button-wrapper">
                    <div class="button">{{this.$store.state.city}}</div>
                    <!-- this.$store.state.city 获取vuex store state里的值-->
                 </div>
              </div>
            </div>
            <div class="area">
              <div class="title border-topbottom">热门城市</div>
              <div class="button-list">
                 <div class="button-wrapper"
                  v-for="(item, key) in hot"
                   :key="key"
                   @click="handleCityClick(item.name)"
                   >
                    <div class="button">{{item.name}}</div>
                 </div>
              </div>
            </div>
            <div class="area"
             v-for="(item, key) of cities"
             :key="key"
             :ref="item.initial"
             >
              <div class="title border-topbottom">{{item.initial}}</div>
              <div class="item-list">
                 <div
                    class="item border-bottom"
                    v-for="(innerItem, innerkey) of item.list"
                    :key="innerkey"
                    @click="handleCityClick(innerItem.name)"
                    >
                {{innerItem.name}}
            </div>
              </div>
            </div>
        </div>
    </div>
</template>

<script>
import Bscroll from 'better-scroll'
// better-scroll 调用滚动插件
export default {
  name: 'cityList',
  props: {
    hot: Array,
    cities: Array,
    letter: String
  },
  methods: {
    handleCityClick (city) {
      this.$store.commit('changeCity', city)
      // 通过$store调用vuex
      this.$router.push('/')
      // $router调用路由跳转页面
    }
  },
  mounted () {
    this.scroll = new Bscroll(this.$refs.wrapper)
    // 生命周期mounted 让wrapper dom 可以滚动
  },
  watch: {
    letter () {
      if (this.letter) {
        const element = this.$refs[this.letter][0]
        this.scroll.scrollToElement(element)
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
  .border-topbottom
   &:before
      border-color:#ccc
   &:after
      border-color:#ccc
  .border-bottom
   &:before
      border-color:#ccc
  .list
    overflow:hidden
    position:absolute
    top:1.58rem
    left:0
    right:0
    bottom:0
    .title
       line-height:.44rem
       background:#eee
       padding-left:.2rem
       color:#666
       font-szie:.26rem
      .button-list
         padding:.1rem  .6rem .1rem .1rem
         overflow:hidden
         .button-wrapper
           float:left
           width:33.3%
          .button
            margin:.1rem
            padding:.1rem 0
            text-align:center
            border: .02rem solid #ccc
            border-radius:.06rem
    .item-list
      .item
        line-height:.76rem
        padding-left:.2rem
</style>
