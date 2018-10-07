<template>
    <div>
         <div class="title">热销推荐</div>
         <ul>
             <li class="item border-bottom" v-for="item of list" :key="item.id">
                <div class="item-wrap">
                     <img class="item-img" :src="item.imgUrl">
                </div>
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                </div>
             </li>
         </ul>
    </div>
   
</template>


<script>
export default {
    name: "HomeWeekend",
    props: {
        list: Array
    }
}
</script>


<style lang="stylus" scoped>
    @import '~styles/mixins.styl'
        .title  
            line-height :.8rem
            background: #eee
            text-indent : .2rem
        .item-wrap
            overflow hidden
            height: 0
            padding-bottom: 33.43%
            .item-img
              width: 100%
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
           
            
</style>
