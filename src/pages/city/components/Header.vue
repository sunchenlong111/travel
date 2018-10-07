<template>
    <div class="header">
        城市选择
        <router-link to="/">
            <div class="iconfont header-back">
                &#xe624;
            </div>
        </router-link>
    </div>    
</template>


<script>
export default {
    name: 'CityHeader'
}
</script>


<style lang="stylus" scoped>
    @import '~styles/varibles.styl'
    .header
        position relative
        overflow hidden
        height $headerHeight
        line-height $headerHeight
        text-align center
        background $bgColor
        font-size 0.32rem
        color #fff
        .header-back
            position absolute
            width .64rem
            left 0
            top 0
            font-size .4rem
            text-align center
            color #fff

</style>

