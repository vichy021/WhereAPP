<template>
  <div>
    <div class="title">周末去哪儿</div>
    <ul>
      <li class="items" v-for="(item,index) in list" :key="item.id">
        <div class="items-img-warp">
          <img class="items-img" :src="item.imgUrl">
        </div>
        <div  class="items-info">
          <p class="items-title">{{item.title}}</p>
          <p class="items-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name:'HomeWeekend',
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
  .items
    overflow:hidden
    height :5.5rem
    .items-img
      width :100%
      height :3.8rem
    .items-info
      line-height :1.4em
      padding :0 .6em
      overflow :hidden
      .items-title
        line-height :2em
        font-size :1.2em
        overflow :hidden
        text-overflow: ellipsis;
        white-space: nowrap;
      .items-desc
        font-size :1.1em
        padding-top :.3em
        color :#ccc
        overflow :hidden
        text-overflow: ellipsis;
        white-space: nowrap;

</style>
