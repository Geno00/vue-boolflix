<template>
    <div class="container">
        <h2>Film</h2>
        <ul>
            <li v-for="(film, index) in films" :key="index" class="item">
                <MyCard :info="film"/>
            </li>
        </ul>
    </div>
  </template>
  
  <script>
  import MyCard from "../elements/MyCard.vue";
  export default {
      name: "FilmsList",
      components: {
          MyCard
      },
      props: {
          films: Array
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