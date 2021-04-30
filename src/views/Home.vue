<template>
  <main v-if="!loading">
    <DataTitle :text="title" :dataDate="dataDate"></DataTitle>
    <DataBoxes :stats="stats"></DataBoxes>
    <CountryData @get-country="getCountry($event)" :countries="countries"></CountryData>
  </main>

  <main v-else>
    <p>Loading....</p>
  </main>
</template>

<script>
import axios from 'axios';
import DataTitle from '@/components/DataTitle.vue'
import DataBoxes from '@/components/DataBoxes.vue'
import CountryData from '@/components/CountryData.vue'

export default {
  components: {
    DataTitle,
    DataBoxes,
    CountryData
  },
  data(){
    return{
      title: 'Global',
      loading: true,
      dataDate: '',
      stats: {},
      countries: []
    }
  },
  methods: {
    getCountry(country){
      this.title = country.Country;
      this.stats = country
    }
  },
  mounted() {
    axios
      .get('https://api.covid19api.com/summary' )
      .then((response) => {
        const summaryData = response.data;
        this.dataDate = summaryData.Date;
        this.stats = summaryData.Global;
        this.countries = summaryData.Countries;
        this.loading = false;
      })
  }
}
</script>
