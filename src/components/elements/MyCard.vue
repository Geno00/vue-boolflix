<template>
  <div class="card">
    <img :src="`https://image.tmdb.org/t/p/w185/${info.poster_path}`" :alt="`${info.original_title || info.original_name}`">

    <div class="card_hover">
        <h4>{{info.title || info.name}}</h4>
        <!-- <img :src="`https://image.tmdb.org/t/p/w185/${info.poster_path}`" :alt="`${info.original_title || info.original_name}`"> -->
        <h5>{{info.original_title || info.original_name}}</h5>
        <div class="flags">
          <img v-if="flags.includes(info.original_language)" :src="require(`../../assets/img/${info.original_language}.png`)" :alt="info.original_language">
          <img v-else src="../../assets/img/none.png" alt="Flag not available">
        </div>

        <div class="ratings">
          <div class="grey-stars">
            <div v-for="rating in 5" :key="rating">
              <i class="fas fa-star"></i>
            </div>
          </div>

          <div class="yellow-stars">
            <div v-for="stars in starRating" :key="stars">
              <i class="fas fa-star"></i>
            </div>
          </div>
        </div>
        <p class="overview">{{info.overview}}</p>
    </div>

  </div>
</template>

<script>
export default {
    name: "MyCard",
    props: {
        info: Object
    },
    data() {
      return {
        flags: [
          "en",
          "es",
          "fr",
          "it"
        ]
      }
    }, 
    computed: {
      starRating() {
        return Math.ceil(this.info.vote_average / 2);
      }
    }
}
</script>

<style lang="scss" scoped>
@import "../../assets/style/partials/variables.scss";
  .card {
    text-align: center;
    position: relative;
    overflow-y: hidden;
  }
  .card_hover {
    padding: 20px 10px;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    opacity: 0;
    background-color: rgba(0, 0, 0, 0.8);
    display: flex;
    flex-direction: column;
    gap: 18px;
    overflow: scroll;
  }
  .card_hover:hover {
    opacity: 1;
  }
  .flags {
    img {
      width: 30px;
      }
  }
  .ratings {
    display: flex;
    position: relative;
    .grey-stars {
      display: flex;
      color: $text-grey;
      & i {
        border: 1px solid $border-grey;
      }
    }
    .yellow-stars {
      display: flex;
      position: absolute;
      top: 0;
      left: 0;
      z-index: 999;
      color: $text-yellow;
        & i {
          border: 1px solid $border-yellow;
        }
    }
  }
</style>