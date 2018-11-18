<template>
  <div>
    <city-header></city-header>
    <city-list
             :list="cityListInfo"
             :cityAllListInfo="cityAllListInfo"
             ></city-list>
  </div>
</template>

<script>
import CityHeader from './header'
import CityList from './cityList'
import axios from 'axios'
export default {
  name: 'city',
  components: {
    CityHeader,
    CityList
  },
  data () {
    return {
      cityListInfo: [],
      cityAllListInfo: []
    }
  },
  methods: {
    getIndexData () {
      axios.get('/api/city.json?city=' + this.$store.state.city)
        .then(this.handleGetDataSucc.bind(this))
        .catch(this.handleGetDataErr.bind(this))
    },
    handleGetDataSucc (res) {
      const data = res.data.data
      this.cityListInfo = data.cityListInfo
      this.cityAllListInfo = data.cityAllListInfo
    },
    handleGetDataErr () {
      console.log('error')
    }
  },
  created () {
    this.getIndexData()
  }
}
</script>
