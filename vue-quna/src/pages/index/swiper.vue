<template>
  <div class='slider-container'>
    <swiper :options='swiperOption'>
      <swiper-slide v-for='item of list' :key='item.id'>
         <img class='slide-img' :src='item.imgUrl' />
      </swiper-slide>
      <div class='swiper-pagination'  slot='pagination'></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'index-swiper',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        loop: true,
        pagination: '.swiper-pagination'
      }
    }
  }
}
</script>

<style lang='stylus' scoped>
 @import '../../assets/stylus/varibles.styl';
 .swiper-pagination >>> .swiper-pagination-bullet-active
   background: $bgColor
 .slider-container
   overflow: hidden
   height: 0
   padding-bottom: 26.67%
 .slide-img
   width: 100%
</style>
