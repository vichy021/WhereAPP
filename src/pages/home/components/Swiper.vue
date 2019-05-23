<template>
  <swiper :options="swiperOption" class="swiper-warp">
    <swiper-slide v-for="item in list" :key="item.id">
      <img class="swiper-img" :src="item.imgUrl"/>
    </swiper-slide>
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
</template>

<script>
  export default {
    name:'HomeSwiper',
    props:{
      list:Array
    },
    data(){
      return {
        swiperOption:{
          pagination:'.swiper-pagination',
          loop:true
        }
      }
    }
  }


</script>
<style lang="stylus">
  /*
    当不加，scorp就可以直接修改组件的样式
  */
  .swiper-pagination-bullet-active
    background-color :white!important
  .swiper-warp
    overflow :hidden
    width :100%
    height :0
    padding-bottom 31.25%
    background-color :#eee
    .swiper-img
      width :100%
</style>
