<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon" >&#xe601;</div>
    </div>
    <div class="header-content">
      <span class="iconfont">&#xe646;</span>
      输入旅游/景点/城市
    </div>
    <router-link to="/city">
      <div class="header-right">
        {{ this.city}}
        <span class="iconfont arrow-icon">&#xe600;</span>
      </div>
    </router-link>

  </div>
</template>

<script>

  export default {
    name: "HomeHeader",
    props:{
      city:String
    }
  }
</script>
<!--
  stylus支持省略花括号，支持省略分号，代码整洁，支持引入，并且支持语法内函数

  {
    在css里面，padding-top,padding-bottom,margin-top,margin-bottom
    取值为百分比的时候，参照的是父元素的宽度。
    padding-bottom:进行提前占位，避免资源加载时候的闪烁，还可以让高度自适应。
  }
   {
    1 rem= html -font-size=50px;//在reset.css中设置成50px
    设计师给的是一个2倍的放大稿
    }
-->
<style lang="stylus"  scoped>
  /*@import "~styles/variable.styl"*/

  .header
    line-height : .86rem
    background-color : #25a4bb
    color white
    display :flex
    .header-left
      width :.64rem
      float:left
      .back-icon
        text-align :center
        font-size :.4rem
    .header-content
      flex :1
      height :.64rem
      line-height : .64rem
      background-color :white
      margin:.12rem
      padding-left :.2rem
      border-radius :.1rem
      color :#cacaca
    .header-right
      width:1.04rem
      color :#fff
      text-align:center
      .arrow-icon
        font-size :.12rem
        margin-left :-.02rem
</style>
