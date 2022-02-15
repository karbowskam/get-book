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

<script lang="ts">
export default {
  name: "Search",
};
</script>

<style lang="scss" scoped>
.searchWrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 22px;
}

.input {
  height: 30px;
  width: 250px;
  border: 0;
  border-bottom: 1px solid rgb(66, 11, 66);
  background: none;
  z-index: 3;
  font-size: 18px;
  font-weight: 400;
  text-align: center;
  color: rgb(66, 11, 66);
  transition: box-shadow 0.5s;

  &:focus {
    outline: none;
    box-shadow: 0 8px 18px -10px rgba(82, 40, 82, 0.6);
  }
}
</style>
