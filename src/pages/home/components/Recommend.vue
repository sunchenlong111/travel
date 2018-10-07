<template>
    <div>
         <div class="title">热销推荐</div>
         <ul>
            <router-link
                tag="li" 
                class="item border-bottom" 
                v-for="item of list" 
                :key="item.id"
                :to="'/detail/' + item.id">
                <img class="item-img" :src="item.imgUrl">
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                    <button class="item-button">查看详情</button>
                </div>
            </router-link>
         </ul>
    </div>
</template>


<script>
export default {
    name: "HomeRecommend",
    props: {
        list : Array
    }
}
</script>


<style lang="stylus" scoped>
    @import '~styles/mixins.styl'
    .title  
        margin-top: .2rem
        line-height :.8rem
        background: #eee
        text-indent : .2rem
    .item
        display: flex
        height: 2.4rem
        .item-img
            height: 2rem
            width: 2rem
            padding: .2rem
        .item-info
            flex:1
            padding: .2rem
            min-width:0
            .item-title
                line-height : .54rem
                font-size: .32rem
                ellipsis() 
            .item-desc
                font-size: .22rem
                color :#ccc
                ellipsis() 
            .item-button
                background:#ff9300
                border-radius: 0.06rem
                font-size:.24rem
                color:#fff
                line-height:.44rem
                margin-top :.2rem
                padding:0 .08rem

            
</style>
