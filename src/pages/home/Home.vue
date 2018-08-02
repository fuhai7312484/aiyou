<template>
<div>
    <home-header></home-header>
    <home-swiper :swiperList="swiperList"></home-swiper>
    <home-icons :iconList="iconList"></home-icons>

 <router-link to="/scancode">
二维码扫码
</router-link>

    <home-recommend :recommendList="recommendList"></home-recommend>
   
    <home-weekend :weekendList="weekendList"></home-weekend>
    </div>
</template>
<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import {mapState} from 'vuex'
import axios from 'axios'
export default {
    name:'Home',
    components: {
        HomeHeader,
        HomeSwiper,
        HomeIcons,
        HomeRecommend,
        HomeWeekend,
    },
    data(){
        return {
            swiperList:[],
            iconList:[],
            recommendList:[],
            weekendList:[],
            lastCity:''

        }
    },
    computed:{
         ...mapState(['city'])
    },
    methods:{
        getHomeInfo(){
            axios.get('/api/index.json?city='+this.city)
            .then(this.getHomeInfoSucc)
        },
        getHomeInfoSucc(res){
            // this.city = res.data.data.city
            res = res.data;
            if(res.ret && res.data){
               
                const arr = res.data;
                //  console.log(data)
                const data = arr.filter(e=>e.city === this.city )[0]
               console.log(data)
                this.swiperList = data.swiperList;
                this.iconList = data.iconList;
                this.recommendList = data.recommendList;
                this.weekendList = data.weekendList;
            }
            // console.log(res)
        },
       

    },
    mounted() {
        this.lastCity = this.city;
        this.getHomeInfo()
       
    },
    activated() {
      if(this.lastCity !== this.city){
        this.lastCity = this.city;
        this.getHomeInfo()
      }
       
    },

}
</script>
<style>
.home{
    font-size: 50px;

}
</style>
