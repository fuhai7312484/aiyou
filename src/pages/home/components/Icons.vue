<template>
<div class="icons">
<swiper :options="swiperOption" v-if="showPages" >
    <swiper-slide v-for="(page,index) of pages" :key="index">
  <div class="icon" v-for="item of page" :key='item.id'>
      <div class="icon-img">
      <img class="icon-content" :src="item.imgUrl"/>
      </div>
      <p>{{item.desc}}</p>

  </div>
  </swiper-slide>

    <div class="swiper-pagination"  slot="pagination"></div>

   
  </swiper>


</div>
    
</template>
<script>
export default {
  name: "HomeIcons",
  props:{
    iconList:Array,
  },
  data() {
    return {
        // swiperOption:{
        //  pagination:'.swiper-pagination',
        // },
       swiperOption: {
     pagination:'.swiper-pagination',
    //  loop:true,
    //  effect : 'cube',
    //   autoplay:true,
     

          // some swiper options/callbacks
          // 所有的参数同 swiper 官方 api 参数
          // ...
        },
      // iconList: [
      //   {
      //     id: "001",
      //     iconUrl:
      //       "http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
      //     desc: "景点门票"
      //   },
      //   {
      //     id: "002",
      //     iconUrl:
      //       "http://img1.qunarzz.com/piao/fusion/1803/bd/9f7b9b2b60c1502.png",
      //     desc: "踏青赏花"
      //   },
      //    {
      //     id: "003",
      //     iconUrl:
      //       "http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
      //     desc: "景点门票"
      //   },
      //   {
      //     id: "004",
      //     iconUrl:
      //       "http://img1.qunarzz.com/piao/fusion/1803/bd/9f7b9b2b60c1502.png",
      //     desc: "踏青赏花"
      //   },
      //    {
      //     id: "005",
      //     iconUrl:
      //       "http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
      //     desc: "景点门票"
      //   },
      //   {
      //     id: "006",
      //     iconUrl:
      //       "http://img1.qunarzz.com/piao/fusion/1803/bd/9f7b9b2b60c1502.png",
      //     desc: "踏青赏花"
      //   },
      //    {
      //     id: "007",
      //     iconUrl:
      //       "http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
      //     desc: "景点门票"
      //   },
      //   {
      //     id: "008",
      //     iconUrl:
      //       "http://img1.qunarzz.com/piao/fusion/1803/bd/9f7b9b2b60c1502.png",
      //     desc: "踏青赏花"
      //   },
      //    {
      //     id: "009",
      //     iconUrl:
      //       "http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
      //     desc: "景点门票"
      //   },
       
      // ]
    };
  },
  computed:{
      pages(){
          const pages = [];
          this.iconList.forEach((e,index) => {
             const page = Math.floor(index/8);
             if(! pages[page]){
                  pages[page] = [];
                               }
             pages[page].push(e);
          });
        
          return pages
      },
      showPages(){
          return this.iconList.length

      }

  }
};
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';
@import '~styles/mixins.styl';
.icons >>>.swiper-container{
    height: 0;
    padding-bottom: 50%;
}
.icons{
    margin-top:.1rem; 
}
.icon {
    float: left;
    width: 25%;
    padding-bottom: 25%;
    overflow: hidden;
    position: relative;
    height: 0;
}

.icon-img {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0.44rem;
    box-sizing: border-box;
    padding: 0.1rem;
    text-align: center;
 
}

.icon-content {
    height: 100%;
}

.icon p {
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
    height: 0.44rem;
    line-height: 0.44rem;
    text-align: center;
    color: $darkTextColor;
 ellipsis()
}


</style>
