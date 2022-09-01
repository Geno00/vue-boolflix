<template>
    <div class="header">
    
      <div class="logo">
        <img src="../../assets/img/boolflix.png" alt="The Boolflix logo">
      </div>
      
      <ul class="navbar">
        <li>Home</li>
        <li>Serie TV</li>
        <li>Film</li>
        <li>Nuovi e popolari</li>
        <li>La mia lista</li>
        <li>Audio e sottotitoli</li>
      </ul>
     
      <form @submit.prevent="$emit('search', searchText)">
        <input type="text" placeholder="Titolo film o serie TV" v-model="searchText" class="input">
        <button class="button">Cerca</button>
      </form>
     
    </div>
  </template>
  
  <script>
  export default {
      name: 'MyHeader',
      data() {
        return {
          searchText: ""
        }
      }
  }
  </script>
  
  <style lang="scss" scoped>
  @import "../../assets/style/global.scss";
  @import "../../assets/style/partials/variables.scss"; 
  .logo {
    img {
      height: 50px;
    }
  }
  .input  {
    width: 250px;
    height: 30px;
    padding: 0 5px;
    margin-right: 10px;
    color: #ffffff;
    border: 2px solid red;
    border-radius: 5px;
    background-color: $background-dark;
  }
  .button {
    height: 30px;
    padding: 0 5px;
    color: $text-white;
    background-color: $background-red;
    border: none;
    border-radius: 5px;
  }
  </style>