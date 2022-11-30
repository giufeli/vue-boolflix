<template>
  <div class="bigContainer">
    <div class="container">
      {{ searchStr }}
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {

  props: {
    searchStr: String,
  },

  created() {
    axios.get('https://api.themoviedb.org/3/search/movie', {
      params: {
        api_key: '160e30b80c1e6ccd305435a3f159b22a',
        query: 'searchStr',
        language: 'it-IT',
      },
    })
      .then((axiosResponse) => {
        console.log(axiosResponse);
      });
  },
};
</script>

<style lang="scss" scoped>
  .bigContainer{
    width: 100%;
    height: calc(100vh - 10vh);
    background-color: rgb(49, 49, 49);
  }

  .container{
    color: white;
  }
</style>
