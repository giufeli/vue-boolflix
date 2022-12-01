<template>
  <div class="navBar">
    <h1>BOOLFLIX</h1>
    <form @submit.prevent="$emit('searchedValue', filmStr)">
      <label for="text">
        <input
          id="searchMovie"
          v-model="filmStr"
          type="text"
          name="searchMovie"
          placeholder="Cerca un titolo"
        >
      </label>
      <button
        type="submit"
      >
        Cerca
      </button>
    </form>
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
    display: flex;
    justify-content: space-around;
    align-items: center;
    width: 100%;
    height: 10vh;
    background-color: rgb(10, 10, 10);
    color: red;
  }

  input, button{
    border-radius: 9px;
    padding: 5px;
    margin-left: 5px;
  }

</style>
