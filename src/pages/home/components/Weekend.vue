<template>
    <div>
      <div class="title">
               周末去哪儿
    </div>
    <ul>
        <li class="item border-bottom" v-for="itme of weekendList" :key="itme.id">
           <div class="item-img-wrapper">
                <img class="item-img" :src="itme.imgUrl"/>
            </div>
            <div class="item-info">
                <p class="item-title">{{itme.title}}</p>
                <p class="item-desc">{{itme.desc}}</p>
              
            </div>
         </li>
    </ul>
     

    </div>
</template>
<script>
export default {
  name: "HomeWeekend",
  props:{
      weekendList:Array,
  },
  data(){
      return {
        //   recommendList:[
        //       {
        //           id:'0001',
        //           imgSrc:'http://img1.qunarzz.com/sight/source/1505/db/b2a56729f39eff.jpg_r_640x214_663a12c6.jpg',
        //           title:'大连圣亚海洋世界',
        //           desc:'浪漫大连首站，浪漫的海洋主题乐园',
        //           url:''
        //       },
        //       {
        //           id:'0002',
        //           imgSrc:'http://img1.qunarzz.com/sight/source/1505/c0/3b002089e244e3.jpg_r_640x214_2da3e67d.jpg',
        //           title:'大连圣亚海洋世界',
        //           desc:'浪漫大连首站，浪漫的海洋主题乐园',
        //           url:''
        //       },
        //        {
        //           id:'0003',
        //           imgSrc:'http://img1.qunarzz.com/sight/source/1505/d1/3070ad726f861b.jpg_r_640x214_39709b85.jpg',
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
.title {
  line-height: 0.8rem;
  background: #eee;
  text-indent: 0.2rem;
}
.item-img-wrapper{
    height:0;
    overflow:hidden;
    padding-bottom:33.9%;
}
.item-img{
    width: 100%;
    
}

.item-info{ 
  
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
