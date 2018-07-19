<template>
<div>
    <home-header></home-header>
    <div class="home">这里是首页</div>
    <router-link to="/list">列表页</router-link>
    </div>
</template>
<script>
import HomeHeader from './components/Header'
export default {
    name:'Home',
    components: {
        HomeHeader,
    }

}
</script>
<style>
.home{
    font-size: 50px;

}
</style>
