<template>
  <!-- 有一个分页没做 -->
    <div class="warp">
      <swiper class="icons">
        <!--  v-for="(page,index) in pages" :key="index" -->
        <swiper-slide>
          <div class="icon"
               v-for="item in list"
               :key="item.id">
            <div class="icon-img">
              <img class="icon-img-content" :src="item.imgUrl"/>
            </div>
            <p class="icon-desc">{{item.desc}}</p>
          </div>
        </swiper-slide>
      </swiper>
    </div>

</template>

<script>
  export default {
    name:'HomeIcons',
    props:{
      list:Array
    }
/*    computed:{
      pages(){
//        定义一个数组，用来分页
        const pages=[];
        const list=this.iconlist;
        if(!list)return;
        list.forEach((item,index)=>{
            const page=Math.floor(index/8);
            if(!pages[page]){
              pages[page]=[];
            }
//            如果存在，就将每个数据添加进当前页中
            pages[page].push(item);
        })
        return pages;
      }
    }*/
  }


</script>
<style lang="stylus">
  .icons
    width :100%
    height :0
    padding-bottom :50%
    margin-top :.5em
    overflow :hidden
    .icon
      position :relative
      width :25%
      height :0
      float :left
      padding-bottom :25%
      overflow :hidden
      .icon-img
        box-sizing :border-box
        position :absolute
        top :0
        left :0
        right:0
        bottom :1.8em
        padding :.4em
        .icon-img-content
          display :block
          height :100%
          margin :0 auto
      .icon-desc
        position absolute
        left :0
        right:0
        bottom :0
        text-align :center
        line-height :1.8em

</style>
