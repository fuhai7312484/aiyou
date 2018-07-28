<template>
<div>
    <router-link tag="div" class="header-abs" to="/" v-show="!showHeader" >
<div class="iconfont header-abs-icon">&#xe624;</div>
    </router-link>

      <div class="header-fixed" 
      v-show="showHeader"
      :style="styleObj"
      >
       景点详情
        <router-link to="/">
       <div class="iconfont header-fixed-icon">&#xe624;</div>
       </router-link>
    </div>
    
    <detail-banner></detail-banner>
    <div class="text-content">


    </div>

</div>
    
</template>
<script>
import DetailBanner from './compoments/Banner'
export default {
    name:'Detail',
    data(){
        return {
            showHeader:false,
            styleObj:{
                opacity:0
            }
        }
    },
    
    components:{
        DetailBanner,
    },
    methods: {
        onScrollTop(){
            let top = document.documentElement.scrollTop;

            if(top > 60){
                
                let opacity =top/110;
                opacity>1?opacity=1:opacity;
                this.styleObj = {opacity};
                 this.showHeader = true;
            
            }else{
                  this.styleObj.opacity = 0;
                this.showHeader = false;
                
            }
           
        },
        
    },
    activated() {
        window.addEventListener('scroll',this.onScrollTop)
    },
    
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.header-abs{
     position:absolute;
     left: .1rem;
     top: .1rem;
      width: .8rem;
      height: .8rem;
      border-radius:.4rem;
       background: rgba(0,0,0,.6);
        color: #fff; 
        z-index: 97;
        text-align: center;
        line-height: .8rem
}

.header-fixed{
   z-index:97;
    height: $headerHeight;
    line-height: $headerHeight;
   
    text-align: center;
    color: #fff;
    background: $bgColor;
    font-size:.32rem;
    position:fixed;
   
    top:0;
    left:0;
    right:0;
}
.header-fixed-icon{
    position:absolute;
    width:0.64rem;
    text-align:center;
    font-size:.4rem;
    top:0;
    left:0;
    color:#fff;
    
}

.text-content{
    height: 50rem;
}


</style>
