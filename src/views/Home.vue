<template>
  <div class="homeWrapper">
    <BackgroundImage>
      <Info />
      <Search v-model="searchValue" @input="handleInput" />
    </BackgroundImage>
  </div>
</template>

<script lang="ts">
import axios from "axios";
import { debounce } from "lodash";
import Info from "@/components/Info.vue";
import Search from "@/components/Search.vue";
import BackgroundImage from "@/components/BackgroundImage.vue";

export default {
  name: "Home",
  components: {
    Info,
    Search,
    BackgroundImage,
  },

  data(): HomeData {
    return {
      searchValue: "",
      results: [],
    };
  },

  methods: {
    handleInput: debounce(function (this: HomeData) {
      console.log(this.searchValue);
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
  min-height: 100vh;
  width: 100%;
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
