<template>
    <div>
        <div class="search">
        <input  
            class="search-input" 
            type="text" 
            placeholder="请输入城市名或拼音" 
            v-model="keyword">
        </div>
        <div class="search-content" ref="search" v-show="keyword">
            <ul>
                <li 
                    class="search-item border-bottom" 
                    v-for="item of list" 
                    :key="item.id"
                    @click="handleCityClick(item.name)"
                    >
                    {{item.name}}
                </li>
                <li class="search-item border-bottom" v-show="hasNoData">
                    没有找到匹配数据
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import Bscroll from 'better-scroll'
import {mapMutations} from 'vuex'
export default {
  name: "CitySearch",
  props: {
      cities: Object
  },
  data () {
      return {
        keyword: '',
        list: [],
        timer: null
      }
  },
  methods: {
       handleCityClick(city){
            this.changeCity(city)
            this.$router.push('/')
        },
        ...mapMutations(['changeCity'])
  },
  computed:{
      hasNoData() {
          return !this.list.length
      }
  },
  watch: {
      keyword () {
          if(this.timer) {
              clearTimeout(this.timer)
          }
          if(!this.keyword){
              this.list = []
              return 
          }
          this.timer = setTimeout(() => {
              const result = []
              for (let i in this.cities){
                  this.cities[i].forEach( (value) => {
                      if (value.spell.indexOf(this.keyword) >-1||
                      value.name.indexOf(this.keyword) >-1) {
                          result.push(value)
                      }
                  })
              }
              this.list = result
          }, 100);
      }
  },
  mounted () {
      this.scroll = new Bscroll(this.$refs.search)
  }
}

</script>


<style lang="stylus" scoped>
    @import '~styles/varibles.styl';
    .search 
        height 0.72rem
        background $bgColor
        padding 0.1rem
        margin-top -0.02rem
        margin-bottom .2rem 
        .search-input
            box-sizing border-box
            padding 0.1rem
            height 0.62rem
            line-height 0.62rem
            border-radius 0.1rem
            width 100%
            text-align center
            color #666
    .search-content
        z-index 1
        overflow hidden
        position absolute
        top 1.58rem
        left 0
        right 0
        bottom 0
        background #ccc
    .search-item
        line-height .62rem
        padding-left 0.2rem
        color #666
       
       
</style>

