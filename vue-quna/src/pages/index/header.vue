<script src="../../router/index.js"></script>
<template>
    <div class="header" ref="header">
      <div class="back iconfont">&#xe600;</div>
      <div class="search">
        <span class="iconfont search-icon">&#xe608;</span>输入城市/景点/游玩主题
      </div>
      <div class="city" @click="handleCityClick">
        {{doubleCity}}
      </div>
    </div>
</template>

<script>
import { mapGetters } from 'vuex'
export default {
  name: 'index-header',
  computed: {
    ...mapGetters(['doubleCity'])
  },
  methods: {
    handleCityClick () {
      this.$refs.header.style.background = "red"
      // this.$router.push('/city')
    },
    test () {
      alert('hello')
    }
  }
}
</script>

<style lang="stylus" scoped>
@import "../../assets/stylus/varibles.styl";
.header
    display: flex
    height: .88rem
    line-height: .88rem
    background: $bgColor
    color: #fff
    .back
      width: .58rem
      line-height: .88rem
      text-align: center
      font-size: .38rem
      font-weight: 900
      padding-left: .1rem
    .search
      flex: 1
      height: .6rem
      line-height: .6rem
      margin: .16rem .1rem
      padding-left: .1rem
      background: #fff
      color: #c2c2c2
      font-size: .26rem
      border-radius: .06rem
      .search-icon
       position: relative
       top: .02rem
       padding: 0 .12rem
    .city
      padding-right: .6rem
      position: relative
      &:after
       position: absolute
       top: .36rem
       right: .2rem
       content: '\0020'
       width: 0
       height: 0
       border-right: .14rem solid transparent
       border-left: .14rem solid transparent
       border-top: .14rem solid #fff
</style>
