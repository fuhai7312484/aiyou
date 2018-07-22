<template>

   <div>
        <city-header></city-header>
        <city-search :cities="cities"></city-search>
        <city-list :cities="cities" :hotCities="hotCities" :letter="letter"></city-list>
        <city-alphabet :cities="cities" @change="handChange"></city-alphabet>
    </div>
</template>
<script>
import CityHeader from "./components/Header";
import CitySearch from "./components/Search";
import CityList from "./components/List";
import CityAlphabet from "./components/Alphabet";
import axios from 'axios'
export default {
  name: "City",
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet,
  },
  data(){
    return {
      cities:{},
      hotCities:[],
      letter:''


    }
  },
  methods:{
    getCityInfo(){
      axios.get('/api/city.json')
      .then(this.getCityInfoSucc)
    },
    getCityInfoSucc(res){
      res = res.data;
      if(res.ret && res.data){
        let data = res.data;
      this.cities = data.cities;
      this.hotCities = data.hotCities;

      }
    },
    handChange(letter){
      this.letter = letter

    }

  },
  mounted () {
    this.getCityInfo()
  }

};
</script>
<style>
</style>

