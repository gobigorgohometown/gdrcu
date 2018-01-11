<template>
    <div class="wrapper">
        <m-header></m-header>
        <m-slider></m-slider>
        <div class="m-content">
            <transition name="move" mode="out-in">
                <router-view></router-view>
            </transition>
        </div>
    </div>
</template>

<script>
    import mHeader from './Mheader.vue'
    import mSlider from './Mslider.vue'

    export default {
        components:{
            mHeader,mSlider
        }
    }
</script>

<style>

</style>
