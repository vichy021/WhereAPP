<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <div class="iconfont header-icon">&#xe601;</div>
    </router-link>

  </div>
</template>

<script>

  export default {
    name: "CityHeader",
  }
</script>

<style lang="stylus"  scoped>
  .header
    position :relative
    line-height :2em
    text-align :center
    font-size :1.2em
    color :white
    background-color :#25a4bb
    .header-icon
      position :absolute
      top :0
      left :.2em
      color :white

</style>

