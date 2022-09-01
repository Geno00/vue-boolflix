<template>
  <div id="app">
    <MyHeader @search="searching"/>
    <MyMain :films="films" :series="series"/>
  </div>
</template>

<script>
import MyHeader from '@/components/sections/MyHeader.vue';
import MyMain from '@/components/sections/MyMain.vue';
import "./assets/style/global.scss"
import axios from 'axios';
export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain
    
  },
  data(){
    return {
      films: [],
      series: []
    }
  },
  methods: {
    searching(payload){
      
      axios.get("https://api.themoviedb.org/3/search/movie", {
        params: {
          api_key: "ef18a7d1778004bb62c8068c3eee6a28",
          query: payload,
          language: "it-IT"
        }
      })
      .then((response) => {
        console.log(response.data.results);
        this.films = response.data.results;
      })
      .catch((error) => {
        console.log(error);
      });
      
      axios.get("https://api.themoviedb.org/3/search/tv", {
        params: {
          api_key: "ef18a7d1778004bb62c8068c3eee6a28",
          query: payload,
          language: "it-IT"
        }
      })
      .then((response) => {
        console.log(response.data.results);
        this.series = response.data.results;
      })
      .catch((error) => {
        console.log(error);
      });
    }
  }
}
</script>

<style lang="scss">

</style>
