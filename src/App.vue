<template>
  <Header @toggle-button="toggleDark" />
  <SearchWord :getData="fetchWord" />
  <Result :word="fetchData" />
</template>

<script>
import Header from "./components/Header.vue";
import SearchWord from "./components/SearchWord.vue";
import Result from "./components/Result.vue";

export default {
  components: {
    Header,
    SearchWord,
    Result,
  },
  data() {
    return {
      fetchData: [],
      text: "",
      isChecked: "",
    };
  },

  methods: {
    toggleDark(value) {
      this.isChecked = value;
      if (this.isChecked) {
        document.documentElement.classList.add("dark");
      } else {
        document.documentElement.classList.remove("dark");
      }
    },
    async fetchWord(text) {
      const res = await fetch(
        `https://api.dictionaryapi.dev/api/v2/entries/en/${text}`
      );
      const data = await res.json();
      [this.fetchData] = data;

      return this.fetchData;
    },
  },
};
</script>

<style></style>
