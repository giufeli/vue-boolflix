<template>
  <div class="navBar">
    <label for="text">
      <input
        id="searchMovie"
        v-model="filmStr"
        type="text"
        name="searchMovie"
        placeholder="Cerca un titolo"
      >
      <button
        type="button"
        @click="$emit('searchedValue',filmStr)"
      >Cerca</button>
    </label>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filmStr: '',
    };
  },
};
</script>

<style lang="scss" scoped>
  .navBar{
    width: 100%;
    height: 10vh;
    background-color: rgb(10, 10, 10);
  }
</style>
