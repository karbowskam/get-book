<template>
  <div class="homeWrapper">
    <Info />
    <Search />
  </div>
</template>

<script lang="ts">
import axios from "axios";
import { debounce } from "lodash";
import Info from "@/components/Info.vue";
import Search from "@/components/Search.vue";

export default {
  name: "Home",
  components: {
    Info,
    Search,
  },

  data(): HomeData {
    return {
      searchValue: "",
      results: [],
    };
  },

  methods: {
    handleInput: debounce(function (this: HomeData) {
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

interface HomeData {
  searchValue: string;
  results: Array<string>;
}
</script>

<style lang="scss" scoped>
.homeWrapper {
  margin: 0;
  padding: 0 32px;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  height: 100vh;
  background-image: url("../assets/books-gb5e5e6791_1920.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: 7% 0%;
}
</style>
