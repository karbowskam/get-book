<template>
  <div class="searchWrapper">
    <input
      type="text"
      class="input"
      id="search__input"
      v-model="searchValue"
      @input="handleInput"
    />
  </div>
</template>

<script>
export default {
  name: "Search",
};
</script>

<style lang="scss" scoped>
.searchWrapper {
  width: 300px;
  display: flex;
  flex-direction: column;
  margin-top: 22px;
}

.input {
  height: 30px;
  border: 0;
  border-bottom: 1px solid black;
  background: none;
}
</style>
