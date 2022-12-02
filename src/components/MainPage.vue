<template>
  <div class="bigContainer">
    <div class="container">
      <h1 v-if="(arrMovies.length)">
        Movies
      </h1>
      <div
        class="boxCard"
      >
        <div
          v-for="obj in arrMovies"
          :key="obj.id"
          class="scheda"
        >
          <div class="flip">
            <div class="title">
              {{ obj.original_title }}
            </div>
            <div>
              Lingua:
              <lang-flag
                class="flag"
                :iso="obj.original_language"
              />
            </div>
            <div>
              <font-awesome-icon
                v-for="item in convertScore(obj.vote_average)"
                :key="item"
                icon="fa-solid fa-star"
                :style="{color:'gold'}"
              />
              <font-awesome-icon
                v-for="item in (maxScore - convertScore(obj.vote_average))"
                :key="item"
                icon="fa-regular fa-star"
                :style="{color:'gold'}"
              />
            </div>
            <div>{{ obj.overview }}</div>
          </div>
          <div class="front">
            <img
              :src="`https://image.tmdb.org/t/p/w500${obj.poster_path}`"
              alt=""
            >
            <div>{{ obj.title }}</div>
          </div>
        </div>
      </div>
      <h1
        v-if="(arrTv.length)"
      >
        Series Tv
      </h1>
      <div
        class="boxCard"
      >
        <div
          v-for="obj in arrTv"
          :key="obj.id"
          class="scheda"
        >
          <div class="flip">
            <div class="title">
              {{ obj.original_name }}
            </div>
            <div>
              Lingua:
              <lang-flag
                class="flag"
                :iso="obj.original_language"
              />
            </div>

            <div>
              <font-awesome-icon
                v-for="item in convertScore(obj.vote_average)"
                :key="item"
                icon="fa-solid fa-star"
                :style="{color:'gold'}"
              />
              <font-awesome-icon
                v-for="item in (maxScore - convertScore(obj.vote_average))"
                :key="item"
                icon="fa-regular fa-star"
                :style="{color:'gold'}"
              />
            </div>

            <div>{{ obj.overview }}</div>
          </div>
          <div class="front">
            <img
              :src="`https://image.tmdb.org/t/p/w342${obj.poster_path}`"
              alt=""
            >
            <div>{{ obj.name }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
  components: {
    LangFlag,
  },
  props: {
    arrMovies: Array,
    arrTv: Array,
  },

  data() {
    return {
      maxScore: 5,
    };
  },

  methods: {
    convertScore(score) {
      const originalMaxScore = 10;
      return Math.round((score * this.maxScore) / (originalMaxScore));
    },
  },
};
</script>

<style lang="scss" scoped>
  .bigContainer{
    min-height: 100vh;
    background-color: rgb(49, 49, 49);
  }
  .container{
    color: red;
    font-size:20px ;
  }

  ul{
    list-style: none;
  }

  img{
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .boxCard{
    display: flex;
    justify-content: space-around;
    align-content: center;
    gap:15px;
    padding-top: 20px;
    color: white;
    flex-wrap: wrap;
  }

  h1{
    padding-top: 80px;
  }

  .flag, .title{
    font-size:20px;
    font-weight: 700;
    margin-bottom: 10px;
  }

  .scheda{
    position: relative;
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-direction: column;
    margin-bottom: 90px;
    height: 350px;
    width: 250px;
  }

  .flip{
    position: absolute;
    padding:10px;
    width: 100%;
    height: 100%;
    margin: auto;
    color: white;
    font-size: 13px;
    font-weight: 300;
    display: none;
  }

  .front{
    width: 100%;
    height: 100%;
    margin: auto;
    text-align: center;
    opacity: 1;

  }
  .front:hover{
    opacity: 0;
  }

  .scheda:hover .flip {
    display: block;
    background-color: rgb(29, 29, 29);
  }

</style>
