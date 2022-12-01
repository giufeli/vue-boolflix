<template>
  <div>
    <HeaderPage @searchedValue="filmName" />
    <MainPage
      :arr-movies="arrMovies"
      :arr-tv="arrTv"
    />
  </div>
</template>
<script>
import HeaderPage from '@/components/headerPage.vue';
import MainPage from '@/components/MainPage.vue';
import axios from 'axios';

export default {

  components: {
    HeaderPage,
    MainPage,
  },

  data() {
    return {
      baseApiUrl: 'https://api.themoviedb.org/3',
      apikey: '160e30b80c1e6ccd305435a3f159b22a',
      resultsLanguage: 'it-IT',
      arrMovies: [],
      arrTv: [],
    };
  },

  methods: {
    filmName(value) {
      axios.get(`${this.baseApiUrl}/search/movie`, {
        params: {
          api_key: this.apikey,
          query: value,
          language: this.resultsLanguage,
        },
      })
        .then((responseAxios) => {
          this.arrMovies = responseAxios.data.results.slice(0, 8);
        });

      axios.get(`${this.baseApiUrl}/search/tv`, {
        params: {
          api_key: this.apikey,
          query: value,
          language: this.resultsLanguage,
        },
      })
        .then((responseAxios) => {
          this.arrTv = responseAxios.data.results.slice(0, 8);
        });
    },
  },
};
</script>

<style lang="scss">
  @import "../node_modules/bootstrap/scss/bootstrap";

  *{
    font-weight: 600;
  }
</style>
