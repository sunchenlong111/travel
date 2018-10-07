<template>
    <div>
        <router-link tag="div" to="/" class="header-abs">
            <div class="iconfont header-abs-back">&#xe624;</div>
        </router-link>
        <div 
            class="header-fixed" 
            v-show="showAbs"
            :style="opacityStyle"
            >
            <router-link to="/">
                <div class="iconfont header-fixed-back">
                    &#xe624;
                </div>
            </router-link>
            景点详情
        </div>
    </div>
</template>

<script>
export default {
   name: 'DetailHeader',
   data () {
       return {
           showAbs:false,
           opacityStyle: {
               opacity: 0
           }
       }
   },
   methods: {
       handleScroll () {
           const top = document.documentElement.scrollTop
           if(top > 60 ){
                let opacity = top /140
                opacity = opacity > 1 ? 1 : opacity
                this.opacityStyle = {opacity}
                this.showAbs = true 
           }
           else{
               this.showAbs = false 
           }
       }
   },
    mounted () {
       window.addEventListener('scroll',this.handleScroll)
   },
    beforeDestroy() {
       window.removeEventListener('scroll',this.hanleScroll)
   }
}
</script>


<style lang="stylus" scoped>
 @import '~styles/varibles.styl'
    .header-abs
        position absolute 
        left .2rem
        top .2rem
        width .6rem
        height .6rem
        line-height .6rem
        text-align center
        border-radius .4rem
        background rgba(0, 0, 0, .8)
    .header-abs-back
        color #fff
        font-size .32rem
    .header-fixed
        z-index 999
        position fixed
        top 0
        left 0
        right 0
        height $headerHeight
        line-height $headerHeight
        text-align center
        background $bgColor
        font-size 0.32rem
        color #fff
        .header-fixed-back
            position absolute
            width .64rem
            left 0
            top 0
            font-size .4rem
            text-align center
            color #fff


</style>


