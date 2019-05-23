<template>
  <div>
    <div class="list" >
      <div class="item"
          v-for="item in Letters"
          :key="item"
          :ref="item"
          @click="handleClick"
          @touchstart="handleTouchStart"
          @touchmove="handleTouchMove"
          @touchend="handleTouchEnd"
      >
          {{item}}
      </div>
    </div>
  </div>

</template>

<script>
  export default {
    name: "CityAlphabet",
    data(){
      return {
        touchStatus: false,
        starY:0,
        timer:null
      }
    },
    props:{
      cities:Object
    },
    computed:{
      Letters () {
        const letters=[];
        for(let i in this.cities){
          letters.push(i);
        }
        return letters;
      }
    },
    updated(){
      this.startY=this.$refs['A'][0].offsetTop;
    },
    methods:{
      handleClick (e) {
//        使用target获取这个e对象
//        console.log(e.target.innerText);
        this.$emit('change',e.target.innerText);
      },
//      这些是HTML5的触摸事件
      handleTouchStart () {
        this.touchStatus=true;
      },
      handleTouchMove (e) {
        if(this.touchStatus){
          if(this.timer){
            clearTimeout(this.timer);
          }
          this.timer=setTimeout(()=>{
            const touchY = e.touches[0].clientY - 76;
            const index = Math.floor((touchY - this.startY)/16);
            if(index >= 0 && index<this.Letters.length)
            this.$emit('change',this.Letters[index-1]);
          },1600);

        }
      },
      handleTouchEnd () {
        this.touchStatus=false;
      }
    }
  }
</script>

<style lang="stylus" scoped>
  .list
    position :absolute
    top :1.86rem;
    right: 0;
    bottom :0
    display :flex
    flex-direction :column
    justify-content :center
    width :.5rem
    overflow :hidden
    .item
      text-align :center
      color :#25a4bb
      height :.33rem
</style>
