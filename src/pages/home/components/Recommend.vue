<template>
  <div>
      <div class="title">热销推荐</div>
      <ul>
        <li class="item" v-for="(item,index) in list" :key="item.id">
          <div class="item-img-warp">
            <img class="item-img" :src="item.imgUrl">
          </div>
          <div  class="item-info">
            <p class="item-title">{{item.title}}</p>
            <p class="item-desc">{{item.desc}}</p>
            <button class="item-button">查看详情</button>
          </div>
        </li>
      </ul>
  </div>
</template>

<script>
    export default {
      name:'HomeRecommend',
      props:{
        list:Array
      }
    }
</script>

<style lang="stylus">
  .title
    margin-top :.5em
    background-color :#F5F5F5
    line-height :2em
    padding-left :.2rem
  .item
    overflow:hidden
    display :flex
    height :1.7rem
    margin :.9em
    .item-img
      width :1.7rem
      height :1.7rem
    .item-info
      line-height :1.4em
      padding :0 .6em
      overflow :hidden
      flex:1
      .item-title
        line-height :1.7em
        font-size :1.2em
        overflow :hidden
        text-overflow: ellipsis;
        white-space: nowrap;
      .item-desc
        font-size :.7em
        line-height :1.8em
        color :#ccc
        overflow :hidden
        text-overflow: ellipsis;
        white-space: nowrap;
      .item-button
        background-color :#FF7400
        color :#ffffff
        border-radius :.3em
        font-size :.7em
        padding :.2em .6em
        margin-top :.8em

</style>
