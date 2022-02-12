<template>
  <div class="home">
    <div class="search">
      <input
        type="text"
        class="search__input"
        id="search__input"
        v-model="searchValue"
        @input="handleInput"
      />
      <ul class="list">
        <li class="list__item" v-for="item in results" :key="item.key">
          {{ item.title }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import axios from "axios";
import { debounce } from "lodash";

export default {
  name: "Home",
  data() {
    return {
      searchValue: "",
      results: [],
    };
  },

  methods: {
    handleInput: debounce(function (this: any) {
      axios
        .get(
          `https://openlibrary.org/search.json?q=${this.searchValue}&_facet=false&_spellcheck_count=0&limit=10&fields=key,cover_i,title,author_name,name&mode=everything`
        )
        .then((response) => {
          this.results = response.data.docs;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>

<style lang="scss" scoped>
.home {
  margin: 0;
  padding: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}

.search {
  width: 300px;
  display: flex;
  flex-direction: column;

  &__input {
    height: 30px;
    border: 0;
    border-bottom: 1px solid black;
  }
}
</style>
