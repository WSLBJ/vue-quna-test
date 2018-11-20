<template>
  <div>
    <div class="location-container">
      <h6 class="area-title">您的位置</h6>
      <div class="location">
        <div class="location-city citySelect" ref="selectCity">
          {{city}}
        </div>
      </div>
    </div>
    <div class="hotCity-container">
      <h6 class="hotCity-title">
        热门城市
      </h6>
      <div class="hotCityList">
        <div class="hotCityListItem" @click="handleHotCityClick" v-for="(item, index) of list" :key="index">
          {{item}}
        </div>
      </div>
      <div class="cityList">
        <div class="cityListItem" v-for="(item, index) of cityAllListInfo" :key="index">
          <h6 class="city-index city-info">{{item.cityIndex}}</h6>
          <div class="city-info" v-for="(items,index) of item.cityItem" :key="index">{{items}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState, mapMutations } from 'vuex'
export default {
  name: 'city-list',
  props: {
    list: Array,
    cityAllListInfo: Array
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    ...mapMutations(['changeCity']),
    handleHotCityClick (e) {
      this.changeCity(e.target.innerText)
      this.$router.go(-1)
    }
  }
}
</script>

<style lang="stylus" scoped>
  .location-container
    height: 1.3rem
    margin-top: .2rem
    padding-left: .4rem
    display: flex
    flex-direction: column
    justify-content: space-between
    .area-title
      color: #616161
    .location
      border-radius: .1rem
      border: .02rem solid #c2c2c2
      color: #c2c2c2
      text-align: center
      width: 1.8rem
      height: .5rem
      line-height: .5rem
  .hotCity-container
    margin-top: .4rem
    padding-left: .5rem
  .hotCityList
    width: 6.4rem
    padding-top: .1rem
    margin-left: -.22rem
    display: flex
    flex-direction: row
    justify-content: space-around
    flex-wrap: wrap
    .hotCityListItem
      width: 30%
      height: .5rem
      line-height: .5rem
      text-align: center
      margin: .2rem 0
  .city-info
    width: 200px
    height: 20px
    padding: 10px 0
    color: #212121
</style>
