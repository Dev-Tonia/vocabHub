<template>
  <div class="flex justify-between items-center dark:text-gray-200">
    <div class="">
      <i class="bx bx-book text-4xl text-gray-400 font-thin"></i>
    </div>
    <div class="flex items-center">
      <h5 class="mr-2">Serif</h5>

      <div
        class="relative inline-block w-6 mr-2 align-middle select-none transition duration-200 ease-in"
      >
        <input
          type="checkbox"
          v-model="isChecked"
          @click="toggleIsDark"
          name="toggle"
          id="toggle"
          class="toggle-checkbox absolute block w-3 h-3 rounded-full bg-white appearance-none border-0 border-white cursor-pointer"
        />
        <label
          for="toggle"
          class="toggle-label block overflow-hidden h-3 rounded-full bg-gray-600 cursor-pointer"
        ></label>
      </div>

      <div class=""><i class="bx bx-moon text-2xl"></i></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isChecked: false,
    };
  },
  methods: {
    toggleIsDark() {
      this.isChecked = !this.isChecked;
      this.$emit("toggle-button", this.isChecked);
    },
  },
};
</script>

<style></style>
