<template>
    <div>
        <div class="banner" @click="handleBannerClick"> 
            <img class="banner-image" 
            :src="bannerImg" >
            <div class="banner-info">
                <div class="banner-title">{{this.sightName}}</div>
                <div class="banner-number">
                    <span class="iconfont banner-icon">&#xe691;</span>
                {{this.bannerImgs.length}}
                </div>
            </div>
        </div>
        <fade-animation>
            <common-gallary 
                :images="bannerImgs" 
                v-show="showGallary"
                @close="handleGallaryClose"
                >
            </common-gallary>
        </fade-animation>
        
    </div>
</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import FadeAnimation from 'common/fade/FadeAnimation'
export default {
    name: 'DetailBanner',
    props: {
        sightName: String,
        bannerImg: String,
        bannerImgs: Array
    },
    data(){
        return {
            showGallary: false
        }
    },
    methods:{
        handleBannerClick(){
            this.showGallary = true
        },
        handleGallaryClose(){
             this.showGallary = false
        }
    },
    components: {
        CommonGallary,
        FadeAnimation
    }
}
</script>


<style lang="stylus" scoped>
    .banner
        position relative
        overflow hidden
        height 0
        padding-bottom 55%
        .banner-image
            width 100%
        .banner-info
            height 0.64rem
            line-height .64rem
            display flex
            position absolute
            left 0
            right 0
            bottom 0
            background-image linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.8))
            .banner-title
                color #fff
                font-size .32rem
                padding 0 .2rem
                flex 1
            .banner-number
                height .32rem
                line-height  .32rem
                margin-top .12rem
                font-size .24rem
                padding 0 .4rem
                border-radius .2rem
                background rgba(0,0,0,0.8) 
                color #fff
                .banner-icon
                    font-size .32rem 
                
           
                
            
                

             
</style>


