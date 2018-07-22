<template>
    <div class="list" ref="wrapper">
        <div>
        <div class="area">
            <div class="title border-topbottom">当前城市</div>
            <div class="button-list">
                <div class="button-wrapper">
                   <div class="button">北京</div>
                    </div>

            </div>
        </div>

         <div class="area">
            <div class="title border-topbottom">热门城市</div>

 <div class="button-list">
                <div class="button-wrapper" 
                v-for="itme of hotCities" 
                :key="itme.id">
               
                   <div class="button">{{itme.name}}{{itme.spell}}</div>
                  </div>
                 
            </div>



        </div>

         <div class="area" 
         v-for="(item,key) of cities"
          :key="key"
          :ref="key"
          >
            
            <div class="title border-topbottom">{{key}}</div>
            <div class="item-list" v-for="e of item" :key="e.id">
                <div class="item border-bottom">
                   {{e.name}}--{{e.spell}}
                </div>
                

            </div>
        </div>


   


        </div>
    </div>
</template>
<script>
import Bscroll from 'better-scroll'
export default {
    name:'CityList',
    props:{
hotCities:Array,
cities:Object,
letter:String,
    },
    mounted() {
        this.scroll = new Bscroll(this.$refs.wrapper)
    },
    watch: {
        letter(){
            if(this.letter){
              
                let el = this.$refs[this.letter][0]
                // console.log(el)
                this.scroll.scrollToElement(el)
            }
    
        }
    }
}
</script>
<style lang="stylus" scoped>
.border-topbottom::before{
    border-color:#ccc; 
}
.border-topbottom::after{
    border-color:#ccc; 
}
.border-bottom::before{
    border-color:#ccc; 
}
.list{
    overflow: hidden;
    position: absolute;
    top:1.58rem;
    left:0;
    right:0;
    bottom: 0;
}
.title{
    line-height: .54rem;
    background: #eee;
    padding-left:.2rem;
    color:  #666;
    font-size: .26rem;
}
.button-list{
     padding: .1rem .6rem .1rem .1rem;
     overflow: hidden;
}
.button-wrapper{
    float: left;
    width: 33.33%;
}
.button{
    text-align: center;
    margin: .1rem;
    border: .02rem solid #00bcd4;
    border-radius:.06rem; 
     padding: .1rem 0;
     color: #00bcd4;
}
.item-list{
    line-height: .76rem;
    color:#666;
    padding-left:.2rem;
}

</style>
