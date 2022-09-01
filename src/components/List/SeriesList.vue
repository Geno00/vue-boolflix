<template>
    <div class="container">
        <h2>Serie TV</h2>
        <ul>
            <li v-for="(serie, index) in series" :key="index" class="item">
                <MyCard :info="serie"/>
            </li>
        </ul>
    </div>
  </template>
  
  <script>
  import MyCard from "../elements/MyCard.vue";
  export default {
      name: "SeriesList",
      components: {
          MyCard
      },
      props: {
          series: Array
      }
  }
  </script>
  
  <style lang="scss" scoped>
  @import "../../assets/style/partials/variables.scss";
  .item {
      width: calc(100% / 6);
      color: $text-white;
  }
  </style>