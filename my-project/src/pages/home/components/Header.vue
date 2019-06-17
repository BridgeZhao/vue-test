<template>
  <div class="header">
    <div class="header-left"><div class="iconfont back-icon">&#xe663;</div></div>
    <div class="header-input"><span class="iconfont">&#xe615;</span>输入城市/景点/游玩主题</div>
    <router-link to="/city">
    <div class="header-right">{{this.$store.state.city}}<span class="iconfont arrow-icon">&#xe652;</span></div>
  </router-link>
  </div>
</template>

<script>
export default {
  name: 'HomeHeader'
  // props: {
  //   city: String
  // }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus" scoped>
.header
 display:flex
 line-height:.86rem
 background:#00bcd4
 color:#fff
 .header-left
   width:.64rem
   float:left
   .back-icon
     text-align:center
     font-size:0.4rem
 .header-input
   flex:1
   height:.64rem
   line-height:0.64rem
   margin-top:.12rem
   margin-left:0.2rem
   background:#fff
   border-radius:0.1rem
   color:#ccc
   padding-left:.2rem
 .header-right
   width:1.24rem
   float:right
   text-align:center
   color:#fff
   .arrow-icon
    font-size:0.24rem
    margin-left:0.1rem
</style>
