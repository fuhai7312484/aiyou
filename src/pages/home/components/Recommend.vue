<template>
    <div>
      <div class="recommend-title">
               热销推荐
    </div>
    <ul>
        <router-link tag="li"
        class="item border-bottom" 
        v-for="itme of recommendList" 
        :key="itme.id"
        :to="'/detail/'+itme.id"
        >
                <img class="item-img" :src="itme.imgUrl"/>
            <div class="item-info">
                <p class="item-title">{{itme.title}}</p>
                <p class="item-desc">{{itme.desc}}</p>
                <button class="item-button">查看详情</button>
            </div>
        </router-link> 
    </ul>
     

    </div>
</template>
<script>
export default {
  name: "HomeRecommend",
  props:{
      recommendList:Array,
  },
  data(){
      return {
        //   recommendList:[
        //       {
        //           id:'0001',
        //           imgSrc:'http://img1.qunarzz.com/sight/p0/1510/a4/a4d95354fde5420e.water.jpg_200x200_cc0042f4.jpg',
        //           title:'大连圣亚海洋世界',
        //           desc:'浪漫大连首站，浪漫的海洋主题乐园',
        //           url:''
        //       },
        //       {
        //           id:'0002',
        //           imgSrc:'http://img1.qunarzz.com/sight/p0/1510/a4/a4d95354fde5420e.water.jpg_200x200_cc0042f4.jpg',
        //           title:'大连圣亚海洋世界',
        //           desc:'浪漫大连首站，浪漫的海洋主题乐园',
        //           url:''
        //       },
        //        {
        //           id:'0003',
        //           imgSrc:'http://img1.qunarzz.com/sight/p0/1510/a4/a4d95354fde5420e.water.jpg_200x200_cc0042f4.jpg',
        //           title:'大连圣亚海洋世界',
        //           desc:'浪漫大连首站，浪漫的海洋主题乐园',
        //           url:''
        //       }
        //   ]

      }

  }
};
</script>

<style lang="stylus" scoped>
@import '~styles/mixins.styl';
.recommend-title {
  margin-top: 0.2rem;
  line-height: 0.8rem;
  background: #eee;
  text-indent: 0.2rem;
}
.item{
    overflow: hidden;
    display: flex;
    height: 1.9rem;
    /* border-bottom:   */
  
}
.item-img{
    width: 1.7rem;
    height: 1.7rem;
    padding:.1rem;
}
.item-info{ 
    flex: 1;
    padding: .1rem;
    overflow:hidden;
}
.item-title{
    line-height: .54rem;
    font-size:.32rem;
    ellipsis();
}
.item-desc{
    
    line-height: .4rem;
    color: #ccc;
    ellipsis();
}
.item-button{
    line-height: .44rem;
    margin-top:.16rem;
    background: #ff9300;
    padding: 0 .2rem;
    border-radius:.06rem;
    color: #fff;
}
</style>
