<template>
<div>
    <div class="banner" @click="showGall">
       <img src="http://img1.qunarzz.com/sight/p0/1609/7a/7ae8ee7831836095a3.water.jpg_600x330_5d562f69.jpg"/>
       <div class="banner-info">
           <div class="banner-title">
                <div class="info-tip">
                    <span class="iconfont">&#xe716;</span>
                   
                    39
                    </div>
              <h1> 大连圣亚海洋世界(AAAA景区)</h1>
           </div>

       </div>
    </div>
<common-gallary :imgs="imgs" v-show="showGallary" @hiddenGall="hiddenGall"></common-gallary>

</div>
</template>
<script>
import CommonGallary from 'common/gallary/Gallary'
export default {
    name:'DetailBanner',
    data(){
        return {
            imgs:['http://img1.qunarzz.com/sight/p0/1803/12/126471e0966aca5ba3.img.jpg_r_800x800_fd14650b.jpg','http://img1.qunarzz.com/sight/p0/1806/5b/5b32a9e1ac462fb5a3.img.jpg_r_800x800_ba8d7dcd.jpg'],
            showGallary:false,
        }
    },
    methods: {
        showGall(){
            this.showGallary = true;
        },
        hiddenGall(){
            
          this.showGallary = false;
        }
    },
    components:{
        CommonGallary,
    },

}
</script>
<style>
.banner{
    overflow: hidden;
    height: 0;
    padding-bottom:55%;
   position: relative;

}
.banner img{
    width: 100%;
}
.banner-info{
      position: absolute;
      display:flex;
      right: 0;
   left:0;
   bottom: 0;
    display: flex;
    line-height: .6rem;
  
    background-image:linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,.8)) 
}
.banner-title{
    flex: 1;
    font-size:.36rem; 
    color: #fff;
    padding: 0 .2rem;
    margin-bottom: .2rem;

}
.info-tip{
    background:rgba(0,0,0,.5);
    max-width: 1rem;
    padding: 0 .1rem; 
    font-size:.1rem; 
    border-radius:1rem; 
    text-align: center;
     color:#fff; 
     line-height: .4rem;
     height: .4rem;
     
}


</style>
