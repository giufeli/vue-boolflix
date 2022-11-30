<template>
  <div>
    <HeaderPage @searchedValue="filmName" />
    <MainPage :search-str="searchStr" />
  </div>
</template>
<script>
import HeaderPage from '@/components/headerPage.vue';
import MainPage from '@/components/MainPage.vue';

export default {

  components: {
    HeaderPage,
    MainPage,
  },
  data() {
    return {
      searchStr: '',
    };
  },

  methods: {
    filmName(value) {
      this.searchStr = value;
    },
  },
};
</script>

<style lang="scss">
  @import "../node_modules/bootstrap/scss/bootstrap";
</style>
