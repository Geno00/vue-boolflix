<template>
    <div class="main">
      <FilmsList :films="films"/>
      <SeriesList :series="series"/>
    </div>
  </template>
  
  <script>
  import FilmsList from '../List/FilmsList.vue';
  import SeriesList from '../List/SeriesList.vue';
  export default {
      name: 'MyMain',
      components: {
        FilmsList,
        SeriesList
      },
      props: {
        films: Array,
        series: Array
      }
  }
  </script>
  
  <style lang="scss" scoped>
  .main {
    height: calc(100vh - 100px); //100px sono l'altezza dell'header
    background-image: url(../../assets/img/boolflix-background.jpeg);
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    overflow-y: scroll;
  }
  </style>