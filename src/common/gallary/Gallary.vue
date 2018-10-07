<template>
    <div class="container" @click="handleGallaryClick">
        <div class="wrapper">
            <swiper :options="swiperOptions">
                <swiper-slide v-for="(item,index) in images" :key="index">
                    <img class="gallary-img" :src="item">
                </swiper-slide>
                <!-- 利用下面的数组循环遍历取出图片 swiper-slide v-for循环遍历，:key值绑定-->
                <div class="swiper-pagination"  slot="pagination"></div>
            </swiper>
        </div>
    </div>
</template>


<script>
export default {
    name: "CommonGallary",
    props: {
        images: {
            type: Array,
            default () {
                return []
            }
        }
    },
    data() {
        return{
            swiperOptions: {
            pagination: '.swiper-pagination',
            paginationType: 'fraction',
            observer:true,
            observeParents:true//监听自身元素或者父级元素dom是否发生了变化，如果变化了的话会刷新  
            }
        }
    },
    methods:{
        handleGallaryClick () {
            this.$emit('close')
        }
    }
}
</script>


<style lang="stylus" scoped>
    .container >>> .swiper-container
        overflow inherit
    .container
        display flex 
        flex-direction column
        justify-content center
        z-index 999
        position fixed
        left 0
        right 0
        top 0
        bottom 0
        background #000
        .wrapper
            width 100%
            height 0
            padding-bottom 100%
            .gallary-img
                width 100%
            .swiper-pagination
                color  #fff
                bottom: -1rem
               
</style>
