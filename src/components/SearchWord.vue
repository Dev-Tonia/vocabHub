<template>
  <div
    class="bg-gray-200 dark:bg-gray-700 flex items-center py-2 rounded-xl px-3 mt-5"
  >
    <input
      type="text"
      v-model="text"
      @keyup.enter="searchWord()"
      @focus="text = ''"
      placeholder="Search Word"
      class="bg-transparent border-none text-gray-800 dark:text-gray-300 font-bold outline-none w-full"
    />
    <i @click="searchWord()" class="bx text-purple-400 bx-search text-2xl"></i>
  </div>
</template>

<script>
export default {
  props: ["getData"],
  data() {
    return {
      text: "word",
    };
  },
  methods: {
    searchWord() {
      if (!this.text) {
        alert("Enter A word");
        return;
      }

      this.getData(this.text);
      // this.text = "";
    },
  },
};
</script>

<style></style>
