<template>
<ul class="list"
 :ref="1"
 >
<li class="item" 
v-for="item of letter" 
:key="item"
:ref="item"
@touchstart="touchStart"
@touchend="touchEnd"
@touchmove="touchMove"
@click="handClick"
>{{item}}</li>
</ul>
    
</template>
<script>
export default {
    name:'CityAlphabet',
    props:{
        cities:Object,
    },
    data(){
        return {
            touchStatus:false,
            startY:0,
            timer:0,
         
        }
    },
    updated() {
        this.startY = this.$refs['1'].offsetTop
      
    },
    computed:{
        letter(){
           const letters = [];
            for(let i in this.cities){
                letters.push(i)
            }
            return letters;
        }


    },
    methods: {
        handClick(ev){
            this.$emit('change',ev.target.innerText)
        },
        touchStart(){
            this.touchStatus = true;
        },
        touchMove(ev){
            if(this.touchStatus){
                if(this.timer){
                    clearTimeout(this.timer)
                }
                this.timer = setTimeout(()=>{
                 
                    const touchY = ev.touches[0].clientY
                    const index =Math.floor((touchY-this.startY)/20)
                    this.$emit('change',this.letter[index])

                },16.7)
      
         
            }

        },
        touchEnd(){
            this.touchStatus = false;
           

        }

    }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl';
.list{
    display:flex;
    flex-direction: column;
    justify-content: center;
    
     position: absolute;
      right:0;
       top: 2.5rem;
       width: .4rem;
      
       
}
.item{
    line-height: .4rem;
    text-align: center;
    color:$bgColor;
}

</style>

