<template>
<div>
    <home-header></home-header>
<home-swiper></home-swiper>
    
    <div class="home">这里是首页</div>
    <router-link to="/list">列表页</router-link>
    </div>
</template>
<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
export default {
    name:'Home',
    components: {
        HomeHeader,
        HomeSwiper,
    }

}
</script>
<style>
.home{
    font-size: 50px;

}
</style>
