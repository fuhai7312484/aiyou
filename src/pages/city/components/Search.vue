<template>
 <div>
    <div class="search">
        <input class="search-input" 
        v-model="keyword" 
        type="text"
        placeholder="输入城市名或拼音"
         />
    </div>
   <div class="search-content" 
   ref="search"
   v-show="keyword"
   >
       <ul>
           <li class="search-item-list border-bottom" v-for="item of list">
           {{item.name}}
           </li>
       </ul>

   </div>
    </div>
</template>
<script>
import Bscroll from 'better-scroll'
export default {
  name: "CitySearch",
  props: {
    cities: Object
  },
  data() {
    return {
      keyword: "",
      list: [],
      timer: null,
     
    };
  },
   mounted() {
    //    console.log(this.$refs)
      
        this.scroll = new Bscroll(this.$refs.search)
    },
  watch: {
    keyword() {
    
      if (this.timer) {
        clearTimeout(this.timer);
      }
      this.timer = setTimeout(() => {
        let result = [];
        for (let index in this.cities) {
          this.cities[index].forEach(e => {
            if (
              e.spell.indexOf(this.keyword) > -1 ||
              e.name.indexOf(this.keyword) > -1
            ) {
              result.push(e);
            }
          });
        }
        let msg = [{id:'000',name:'没有您查询的城市信息！',spell:'没有您查询的城市信息！'}]
        result.length?this.list = result:this.list=msg;
     
      }, 100);
    }
  }
};
</script>
 <style lang="stylus" scoped>
 @import '~styles/varibles.styl';

 .search {
     padding: 0 0.1rem;
     height: 0.72rem;
     background: $bgColor;
 }

 .search-input {
     box-sizing: border-box;
     width: 100%;
     text-align: center;
     height: 0.62rem;
     line-height: 0.62rem;
     border-radius: 0.06rem;
     color: #666;
     padding: 0 0.1rem;
 }

 .search-content {
     z-index: 1;
     overflow: hidden;
     position: absolute;
     top: 1.58rem;
     left: 0;
     right: 0;
     bottom:0;
     background:#fff;
 }
 .search-item-list{
       line-height: .76rem;
    color:#666;
    padding-left:.2rem;
 }
</style>

