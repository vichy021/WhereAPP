<template>
  <div>
    <div class="search">
      <input class="search-input" v-model="keywords" type="text" placeholder="输入城市名或者拼音"/>

    </div>
    <div class="search-content" ref="search"  v-show="keywords">
      <ul>
        <li  class="search-item" v-for="item of list">
          {{ item.name}}
        </li>
        <li v-if="!list.length">没有找到匹配数据</li>
      </ul>
    </div>
  </div>

</template>

<script>
  import BScroll from 'better-scroll'
  export default {
    name: "CitySearch",
    props:{
      cities:Object
    },
    data(){
      return {
        keywords:'',
        list:[],
        timer:null
      }
    },
    mounted(){
      this.scroll=new BScroll(this.$refs.search);
    },
    watch:{
      keywords(){
//        节流函数
        if(this.timer){
          clearTimeout(this.timer);
        }
        this.timer=setTimeout(()=>{
          const result=[];
          if(!this.keywords){
            this.list=[];
            return;
          }
          for(let i in this.cities){
            this.cities[i].forEach((value)=>{
              if(value.spell.indexOf(this.keywords) > -1|| value.name.indexOf(this.keywords) > -1){
                result.push(value);
              }
            })
          }
          this.list=result;
        },10)

      }
    }
  }
</script>

<style lang="stylus"  scoped>
  .search
    background-color :#25a4bb
    height :2.4em
    padding :.1rem
    .search-input
      box-sizing :border-box
      width :98%
      margin-left :.06rem
      padding :0 .2rem
      height :2em
      line-height :2.4em
      text-align :center
      border-radius :.3em
  .search-content
    z-index :1
    position :absolute
    top :1.5rem
    left :0
    right :0
    bottom :0
    background-color :#eaeaea
    overflow :hidden
    .search-item
      background-color :#ffffff
      line-height :.4rem
      padding :.1rem
</style>

