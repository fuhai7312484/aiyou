<template>
<div class="wrapper">
    
 <swiper :options="swiperOption" ref="mySwiper" 
 >
    <!-- slides -->
    <swiper-slide v-for="itme of swiperList" :key="itme.id">
        <img class="swiper-img" :src="itme.imgUrl" alt=""/>
        </swiper-slide>
    <!-- <swiper-slide><img class="swiper-img" src="" alt=""/></swiper-slide> -->
  
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
</div>
</template>
<script>

// var mySwiper = new Swiper('.swiper-pagination', {
//   autoplay:true,//等同于以下设置
//   /*autoplay: {
//     delay: 3000,
//     stopOnLastSlide: false,
//     disableOnInteraction: true,
//     },*/
// });

// import './images/swiper1.jpg'
export default {
    name:'HomeSwiper',
    data (){
        return {

 swiperOption: {
     pagination:'.swiper-pagination',
     loop:true,
    //  effect : 'cube',
    //   autoplay:true,
          // some swiper options/callbacks
          // 所有的参数同 swiper 官方 api 参数
          // ...
        },
        swiperList:[
            {
                id:'0001',
                imgUrl:'http://img1.qunarzz.com/piao/fusion/1807/ac/90964489249b4302.jpg_750x200_fc7865fa.jpg'
            },
            {
                id:'0002',
                imgUrl:'http://img1.qunarzz.com/piao/fusion/1708/f1/ee65a13642c95c02.jpg_750x200_3440fec0.jpg'
            },
              {
                id:'0003',
                imgUrl:'http://img1.qunarzz.com/piao/fusion/1807/a1/41a802abfc4f0202.jpg_750x200_9f0cf69c.jpg'
            }
        ]
        }
    },
    computed:{
         swiper() {
        return this.$refs.mySwiper.swiper
      }
    },
      mounted() {
      // current swiper instance
      // 然后你就可以使用当前上下文内的swiper对象去做你想做的事了
      console.log('this is current swiper instance object', this.swiper)
      this.swiper.slideTo(3, 1000, false)
    }
}
</script>
<style lang="stylus" scoped>
.wrapper>>>.swiper-pagination-bullet-active{
    background:#fff;
    
}
.wrapper{
    width:100%;
    height:0;
    overflow:hidden;
    padding-bottom:27%;
    background #eee;

}

.swiper-img{
    width:100%;

}

</style>
