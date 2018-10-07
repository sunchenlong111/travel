<template>
    <div class="wrapper">
        <swiper :options="swiperOption" v-if="showSwiper">
            <swiper-slide v-for="item of list" :key="item.id">
                <img class="swiper-img" :src="item.imgUrl">
            </swiper-slide>
            <!-- 利用下面的数组循环遍历取出图片 swiper-slide v-for循环遍历，:key值绑定-->
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
</template>


<script>
export default {
    name: 'HomeSwiper',
    props: {
        list: Array
    },
    data() {
        return {
            swiperOption: {
                pagination: '.swiper-pagination',
                loop: true
            }
        }
    },
    computed: {
        showSwiper () {
            return this.list.length
        }
    }
}
</script>



<style lang="stylus" scoped>
    .wrapper >>> .swiper-pagination-bullet //穿刺效果，因为.swiper-pagination-bullet不在当前组件，但是是
    //当前组件的后代元素，利用>>>穿刺效果找到下属，并赋值css属性
        background: #fff !important
    .wrapper
        overflow: hidden
        width: 100%
        height: 0
        padding-bottom: 31.25%
        background:#eee
        .swiper-img
            width:100%
</style>
