<template>
    <div class="header">
    选择城市
    <router-link to="/">
       <div class="iconfont header-back">&#xe663;</div>
    </router-link>
</div>
</template>

<script>
export default {
  name: 'cityHeader'
}
</script>

<style lang="stylus" scoped>
.header{
   position:relative
   overflow:hidden
   height:.86rem
   line-height:.86rem
   text-align:center
   color:#fff
   background:#00bcd4
   font-size:.32rem
   .header-back{
      position:absolute
      top:0
      left:0
      width:1.24rem
      text-align:center
      font-size:.4rem
      color:#fff
   }
}
</style>
