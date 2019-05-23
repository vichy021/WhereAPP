<template>
  <div>
    <city-header></city-header>
    <city-search :cities="cities"></city-search>
    <city-list :cities="cities" :hot="hotCities" :letter="letter"></city-list>
    <city-alphabet :cities="cities" @change="handleClick"></city-alphabet>

  </div>
</template>

<script>
  //   这是一个局部组件
  import CityHeader from './components/Header.vue'
  import CitySearch from './components/Search.vue'
  import CityList from './components/List.vue'
  import CityAlphabet from './components/Alphabet.vue'
  import axios from 'axios'
  export default {
    name: "city",
    data(){
      return {
        hotCities:[],
        cities:{},
        letter:''
      }
    },
    components: {
      CityHeader,
      CitySearch,
      CityList,
      CityAlphabet
    },
    methods:{
      getCityInfo(){
        axios.get('/static/mock/city.json').then(this.getCityInfoSucc);
      },
      getCityInfoSucc(res){
        res =res.data;
        if(res.ret && res.data){
          const data=res.data;
          this.hotCities=data.hotCities;
          this.cities=data.cities;
        }
      },
      handleClick(letter){
        this.letter=letter;
      }
    },
    mounted(){
      this.getCityInfo();
    },
  }

</script>

<style>
  .city{
    font-size: 20px;
  }
</style>
