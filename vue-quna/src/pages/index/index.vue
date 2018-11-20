<script src="../../main.js"></script>
<script src="../../router/index.js"></script>
<template>
 <div>
     <index-header ref="header"></index-header>
     <index-swiper :list="swiperInfo"></index-swiper>
     <index-icons :list="iconsInfo"></index-icons>
     <index-sights :list="sightsInfo"></index-sights>
 </div>
</template>

<script>
import IndexHeader from './header'
import IndexSwiper from './swiper'
import IndexIcons from './icons'
import IndexSights from './sights'
import { mapState, mapActions } from 'vuex'
import axios from 'axios'
export default {
  name: 'index',
  components: {
    IndexHeader,
    IndexSwiper,
    IndexIcons,
    IndexSights
  },
  data () {
    return {
      swiperInfo: [],
      iconsInfo: [],
      sightsInfo: []
    }
  },
  computed: {
    ...mapState({
      city: 'city'
    })
  },
  methods: {
    ...mapActions({
      delayCity: 'changeCityDelayFiveSeconds'
    }),
    getIndexData () {
      axios.get('/api/index.json?city=' + this.city)
        .then(this.handleGetDataSucc.bind(this))
        .catch(this.handleGetDataErr.bind(this))
    },
    handleGetDataSucc (res) {
      const data = res.data.data
      this.swiperInfo = data.swiperList
      this.iconsInfo = data.iconList
      this.sightsInfo = data.sightsList
      if (!this.city) {
        this.delayCity(data.city)
      }
    },
    handleGetDataErr () {
      console.log('error')
    }
  },
  created () {
    this.getIndexData()
  },
  mounted () {
    this.$refs.header.test()
  },
  watch: {
   city () {
      this.getIndexData()
    }
  }
}
</script>

<style></style>
