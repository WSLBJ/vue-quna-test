<template>
  <div class="sights">
    <div>
     <div v-for="item of list" :key="item.id">
        <div>
          <img :src="item.imgUrl" alt="" />
        </div>
     </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'index-sights',
  props: {
    list: Array
  },
  data () {
    return {
    }
  },
  mounted () {
    this.scroll = new BScroll('.sights')
  }
}
</script>
<style lang="stylus" scoped>
   .sights
     overflow: hidden
     height: 10rem
     background: green
</style>
