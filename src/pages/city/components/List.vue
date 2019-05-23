<template>

    <div class="list" ref="wrapper">
      <div>
        <div class="area">
          <div class="title">当前城市</div>
          <div class="button-list">
            <div class="button-hot">北京</div>
          </div>
        </div>

        <div class="area">
          <div class="title">热门城市</div>
          <div class="button-list" >
            <div class="button-list-wrap" v-for="item in hot" :key="item.id">
              <div class="button">{{ item.name }}</div>
            </div>

          </div>
        </div>

        <div class="area"  v-for="(list, key) in cities" :key="key" :ref="key">
          <div class="title">
            {{key}}
          </div>
          <div class="item-list"
               v-for="innerItem in list"
               :key="innerItem.id"
          >
            <div class="item">{{ innerItem.name }}</div>
          </div>
        </div>

      </div>

    </div>
</template>

<script>
  import BScroll from 'better-scroll'
  export default {
    name: "CityList",
    props:{
      hot:Array,
      cities:Object,
      letter:String
    },
    mounted(){
      this.scroll=new BScroll(this.$refs.wrapper);
    },
    watch:{
      letter (){
       if(this.letter){
         const element=this.$refs[this.letter][0];
         this.scroll.scrollToElement(element);
       }
      }
    }
  }
</script>

<style lang="stylus" scoped>
  .list
    overflow :hidden
    position :absolute
    top :1.5rem
    left :0
    right :0
    bottom :0
    .title
      background-color :#F5F5F5
      line-height :2em
      border-bottom :.01em solid #cacaca
      padding-left :.2rem
    .button-list
      overflow :hidden
      padding :.1rem
      .button-hot
        width :28%
        padding :.1rem 0
        margin :0 .1rem
        border :.02rem solid #ccc
        border-radius :.3em
        text-align :center
      .button-list-wrap
        float :left
        padding :.1rem 0
        margin :0 .1rem
        width :28%
        .button
          width :100%
          padding :.1rem 0
          border :.02rem solid #ccc
          border-radius :.3em
          text-align :center
    .item-list
      .item
        line-height :.4rem
        padding :.1rem
        border-top :.01em solid #EBEBEB



</style>
